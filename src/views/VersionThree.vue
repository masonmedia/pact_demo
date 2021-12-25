<template>
  <div class="container-fluid position-relative">
    <!-- swipe layer -->
    <div class="animate__animated animate__slideOutRight h-100 w-100 position-absolute start-0"
    style="background: #000; z-index: 1000"></div>
    <!-- banner -->
    <div class="container-fluid mt-5"
    :style="{'background' : 'url(' + require(`@/${text.banner}`) +')', 'background-size' : 'cover' }">
      <div class="row min-vh-100 justify-content-start align-items-center p-5">
        <div class="col-lg-8 text-focus-in">
          <div class="d-flex flex-column justify-content-center align-items-start p-5"
            style="background: rgba(0,0,0,0.6); backdrop-filter: blur(10px); border-radius: 33px; min-height: 50vh">
            <h1 class="fw-bold text-uppercase lh-1 text-light m-0"
              style="filter: drop-shadow(3px 3px 5px #000); font-size: 5vmin;">
              {{ text.page_2.page_title }}
            </h1>
            <svg xmlns="http://www.w3.org/2000/svg" width="36" height="36" fill="currentColor"
              class="bi bi-chevron-double-down text-white mt-3 animate__animated animate__fadeInUp animate__delay-1s"
              viewBox="0 0 16 16">
              <path fill-rule="evenodd"
                d="M1.646 6.646a.5.5 0 0 1 .708 0L8 12.293l5.646-5.647a.5.5 0 0 1 .708.708l-6 6a.5.5 0 0 1-.708 0l-6-6a.5.5 0 0 1 0-.708z" />
              <path fill-rule="evenodd"
                d="M1.646 2.646a.5.5 0 0 1 .708 0L8 8.293l5.646-5.647a.5.5 0 0 1 .708.708l-6 6a.5.5 0 0 1-.708 0l-6-6a.5.5 0 0 1 0-.708z" />
            </svg>
          </div>
        </div>
      </div>
    </div>

    <div class="container-fluid py-5 bg-light">
      <div class="row">
        <!-- carousel mobile title -->
        <div class="col-lg-12 d-flex d-md-none justify-content-start align-items-center text-left pt-3">
          <h2 class="fw-bold text-uppercase" style="color: #53565a;" v-html="text.page_2.carousel_title"></h2>
        </div>
        <!-- carousel vertical title -->
        <div :class="isActive ? 'position-absolute z--1' : ''"
          class="col-md-2 d-none d-md-flex justify-content-center align-items-center position-relative border-top border-bottom border-end text-secondary text-center"
          style="border-radius: 0 33px 33px 0; background: #ACCEC8">
          <p class="rotate-90" v-html="text.page_2.carousel_title"></p>
        </div>
        <div :class="isActive ? 'col-md-12' : 'col-md-10'"
          class="d-flex justify-content-center align-items-center text-center">
          <!-- carousel -->
          <swiper class="swiper py-3" :options="swiperOption" @slideChangeTransitionStart="slideStart">
            <button :class="isActive ? 'puff-out-center' : ''"
              class="btn btn-sm btn-light position-absolute start-50 translate-middle shadow text-uppercase"
              style="width: 50px; height: 50px; top: 20%; border-radius: 100%; z-index: 10; font-size: 11px">
              {{ text.carousel_drag }}
            </button>
            <swiper-slide style="filter: drop-shadow(3px 3px 5px lightgrey)"
              v-for="slide in text.page_2.carousel_slides" :key="slide.id">
              <!-- slide -->
              <div class="card" style="min-height: 450px; border-radius: 33px 33px 0 0;">
                <img :src="require(`@/${slide.img}`)" class="card-img-top" style="border-radius: 33px 33px 0 0;">
                <div class="card-body bg-light text-start py-4">
                  <span class="badge bg-primary">{{ slide.category }}</span>
                  <p class="lh-sm fw-bold pr-5 pb-2 border-bottom" style="color: #00000080">{{ slide.title }}</p>
                  <p class="small lh-sm fw-light pr-5" style="color: #00000050">{{ slide.text }}</p>
                  <a href="#" class="text-decoration-none text-secondary">{{ text.page_2.carousel_cta }}
                    <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor"
                      class="bi bi-chevron-double-right text-secondary" viewBox="0 0 16 16">
                      <path fill-rule="evenodd"
                        d="M3.646 1.646a.5.5 0 0 1 .708 0l6 6a.5.5 0 0 1 0 .708l-6 6a.5.5 0 0 1-.708-.708L9.293 8 3.646 2.354a.5.5 0 0 1 0-.708z" />
                      <path fill-rule="evenodd"
                        d="M7.646 1.646a.5.5 0 0 1 .708 0l6 6a.5.5 0 0 1 0 .708l-6 6a.5.5 0 0 1-.708-.708L13.293 8 7.646 2.354a.5.5 0 0 1 0-.708z" />
                    </svg>
                  </a>
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
      <div class="container shadow-lg mb-3" style="background: rgba(0,0,0,0.2); border-radius: 33px;">
        <!-- row 1 -->
        <div class="row d-flex justify-content-center align-items-center" style="min-height: 75vh">
          <div class="col-lg-6 align-self-center p-5">
            <h2 class="fw-bold lh-1 text-uppercase" style="font-size: 6vmin">{{ text.page_2.text_section.title }}</h2>
          </div>
          <div class="col-lg-6 align-self-stretch p-0" style="min-height: 50vh;">
            <img src="../assets/banner1.jpg" class="w-100 h-100" style="object-fit: cover; border-radius: 0 33px 33px 0"
              alt="">
          </div>
        </div>
      </div>
      <!-- row 2 -->
      <div class="container shadow-lg" style="background: #ACCEC8; border-radius: 33px">
        <div class="row d-flex justify-content-center align-items-center" style="min-height: 75vh">
          <div class="col-lg-6 align-self-stretch p-0" style="min-height: 50vh;">
            <img src="../assets/banner1.jpg" class="w-100 h-100" style="object-fit: cover; border-radius: 33px 0 0 33px"
              alt="">
          </div>
          <div class="col-lg-6 align-self-center p-5">
            <h2 class="fs-4 fw-lighter lh-sm">{{ text.page_2.text_section.text }}</h2>
            <button class="btn btn-sm btn-outline-dark rounded-pill mt-3 px-4"
              @click="$router.push({ path: '/' })">{{ text.global_cta }}</button>
          </div>
        </div>
      </div>
    </div><!-- end main container -->
  </div>
</template>

<script>
  import { Swiper, SwiperSlide } from 'vue-awesome-swiper'
  import text from '@/text.json'

  export default {
    name: 'VersionThree',
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