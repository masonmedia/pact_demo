<template>
  <div class="container-fluid py-5 bg-light">
    <div class="animate__animated animate__slideOutRight bg-dark h-100 w-100 position-absolute start-0" style="z-index: 1000"></div>
    <div class="row px-5 pt-5 pb-3 pb-md-5">
      <div class="col-lg-12 pt-5">
        <h1 class="animate__animated animate__flipInX fw-bold text-uppercase lh-1 text-light"
          style="-webkit-text-stroke: 1.5px grey; color: transparent; font-size: 9vmin;">
          <span class="px-0 px-md-5"></span>{{ text.page_2.page_title }}
        </h1>
      </div>
      <div class="col-lg-12 d-flex d-md-none justify-content-start align-items-center text-left pt-3">
        <h2 class="fw-bold text-uppercase" style="color: #53565a;" v-html="text.page_2.carousel_title"></h2>
      </div>
    </div>
    <div class="row">
      <!-- carousel vertical title -->
      <div :class="isActive ? 'position-absolute z--1' : ''"
        class="col-md-2 d-none d-md-flex justify-content-center align-items-center position-relative border-top border-bottom border-end text-secondary text-center"
        style="border-radius: 0 33px 33px 0; background: #d6d6d650">
        <p style="transform: rotate(-90deg)" v-html="text.page_2.carousel_title"></p>
      </div>
      <div :class="isActive ? 'col-md-12' : 'col-md-10'"
        class="d-flex justify-content-center align-items-center text-center">
        <!-- carousel -->
        <swiper class="swiper py-3" :options="swiperOption" @slideChangeTransitionStart="slideStart"
          @reachEnd="slideEnd">
          <button :class="isActive ? 'puff-out-center' : ''"
            class="btn btn-sm btn-light position-absolute start-50 translate-middle shadow text-uppercase"
            style="width: 50px; height: 50px; top: 20%; border-radius: 100%; z-index: 10; font-size: 11px">
            {{ text.carousel_drag }}
          </button>
          <swiper-slide style="filter: drop-shadow(3px 3px 5px lightgrey)" v-for="slide in text.page_2.carousel_slides"
            :key="slide.id">
            <!-- slide -->
            <div class="card" style="min-height: 450px; border-radius: 33px 33px 0 0;">
              <img :src="require(`@/${slide.img}`)" class="card-img-top" style="border-radius: 33px 33px 0 0;">
              <div class="card-body bg-light text-start py-4">
                <span class="badge bg-primary">{{ slide.category }}</span>
                <p class="lh-sm fw-bold pr-5 pb-2 border-bottom" style="color: #00000080">{{ slide.title }}</p>
                <p class="small lh-sm fw-light pr-5" style="color: #00000050">{{ slide.text }}</p>
                <a href="#" class="text-decoration-none text-primary">{{ text.page_2.carousel_cta }}</a>
              </div>
            </div>
          </swiper-slide>
          <div class="swiper-pagination" slot="pagination"></div>
        </swiper>
      </div>
    </div>

    <!-- spacer -->
    <div class="py-4 my-2"></div>

    <!-- text div -->
    <div class="container p-5 shadow-lg text-light bg-secondary" style="border-radius: 33px">
      <div class="row d-flex justify-content-center align-items-center py-3">
        <div class="col-lg-6 align-self-center px-4">
          <h2 class="fw-bold lh-1 text-uppercase" style="font-size: 6vmin">{{ text.page_2.text_section.title }}</h2>
        </div>
        <div class="col-lg-6 align-self-center px-4">
          <p class="my-4">{{ text.page_2.text_section.text }}</p>
          <button class="btn btn-outline-light text-uppercase m-0 px-4"
          @click="$router.push('/three')"
          style="border-radius: 33px;">{{ text.page_2.text_section.cta }}</button>
        </div>
      </div>
    </div>

  </div><!-- end main container -->
</template>

<script>
import { Swiper, SwiperSlide } from 'vue-awesome-swiper'
import axios from 'axios'
import text from '@/text.json'

  export default {
    name: 'VersionTwo',
    components: {
      Swiper,
      SwiperSlide
    },
    data() {
      return {
        text: text,
        data: [],
        errors: [],
        isActive: false,
        swiperOption: {
          slidesPerView: 2,
          spaceBetween: 10,
          centeredSlides: false,
          grabCursor: true,
          pagination: {
            el: '.swiper-pagination',
            clickable: true
          },
          freeMode: {
            enabled: true,
            sticky: true,
          },
          breakpoints: {
            '@0.75': {
              slidesPerView: 2,
            },
            '@1.0': {
              slidesPerView: 3,
            },
            '@1.5': {
              slidesPerView: 4,
            },
          }
        }
      }
    },
    methods: {
      slideStart() {
        console.log("slide started")
        this.isActive = true

      },
      slideEnd() {
        console.log("slider ended")
        this.isActive = false

      }
    },
    created() {
      axios.get('https://jsonplaceholder.typicode.com/photos')
        .then(response => {
          this.data = response.data
          console.log(this.data)
        })
        .catch(e => {
          this.errors.push(e)
        })
    },
  }
</script>

<style lang="scss" scoped>
  .card-img-top {
    border-radius: 33px 33px 0 0;
  }

  .card-body {
    border-radius: 0 0 33px 0px;
  }

  .swiper-slide,
  .card {
    width: 100%;
    border-radius: 33px 33px 33px 0 !important;
  }

  .z--1 {
    z-index: -1;
  }
</style>