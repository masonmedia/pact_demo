<template>
    <div>
    <div class="animate__animated animate__slideOutRight bg-dark h-100 w-100 position-absolute start-0" style="z-index: 1000;"></div>
    <div class="container-fluid py-5 bg-dark">
        <div class="row p-5">
            <div class="col-lg-12 pt-5">
                <h1 class="knockout fw-bold text-uppercase lh-1 bounce-in-top" style="font-size: 9vmin; color: #FFFAF340;"
                    v-html="text.page_1.page_title">
                </h1>
            </div>
        </div>
        <div class="row">
            <!-- carousel vertical title -->
            <div
            class="col-md-2 d-none d-md-flex justify-content-center align-items-center border-top border-end border-bottom border-secondary text-light text-center"
            :class="isActive ? 'position-absolute z--1' : ''"
            style="border-radius: 0 33px 33px 0">
                <p v-html="text.page_1.carousel_title"></p>
            </div>
            <!-- carousel -->
            <div :class="isActive ? 'col-md-12' : 'col-md-10'"
            class="d-flex justify-content-center align-items-center text-center">
                <swiper class="swiper"
                :options="swiperOption" @slideChangeTransitionStart="slideStart"
                @reachEnd="slideEnd">
                    <button :class="isActive ? 'puff-out-center' : ''"
                    class="btn btn-sm btn-light position-absolute start-50 translate-middle shadow text-uppercase"
                    style="width: 50px; height: 50px; top: 20%; border-radius: 100%; z-index: 10; font-size: 11px">
                    {{ text.carousel_drag }}
                    </button>
                    <swiper-slide class="shadow" v-for="(slide, index) in text.page_2.carousel_slides" :key="index">
                    <!-- <swiper-slide class="shadow" v-for="slide in data.slice(0, 20)" :key="slide.id"> -->
                        <!-- slide -->
                        <div class="card border-secondary bg-dark"
                            style="min-height: 450px; border-radius: 33px 33px 33px 0;">
                            <img :src="require(`@/${slide.img}`)" class="card-img-top" style="border-radius: 33px 33px 0 0;">
                            <div class="card-body bg-dark text-light text-start py-4"
                            style="border-radius: 0 0 33px 0;">
                            <span class="badge bg-primary p-2 mb-3">{{ slide.category }}</span>
                            <p class="lh-sm fw-bold text-light pr-5 pb-2 border-bottom">{{ slide.title }}</p>
                            <p class="small lh-sm fw-light text-light pr-5">{{ slide.text }}</p>
                            <a href="#" class="text-decoration-none text-light">{{ text.page_2.carousel_cta }} 
                                <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-chevron-double-right text-light" viewBox="0 0 16 16">
                                    <path fill-rule="evenodd" d="M3.646 1.646a.5.5 0 0 1 .708 0l6 6a.5.5 0 0 1 0 .708l-6 6a.5.5 0 0 1-.708-.708L9.293 8 3.646 2.354a.5.5 0 0 1 0-.708z"/>
                                    <path fill-rule="evenodd" d="M7.646 1.646a.5.5 0 0 1 .708 0l6 6a.5.5 0 0 1 0 .708l-6 6a.5.5 0 0 1-.708-.708L13.293 8 7.646 2.354a.5.5 0 0 1 0-.708z"/>
                                </svg>
                            </a>
                                <!-- <p class="text-uppercase" style="font-size: 16px">Category</p>
                                <p class="small lh-sm fw-light pr-5" style="color: lightgrey">
                                {{ slide.title.slice(0, 40) }}</p>
                                <a href="#" class="btn btn-outline-light">More</a> -->
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
        <div class="container p-5 rounded" style="background: #ACCEC8;">
            <div class="row d-flex justify-content-center align-items-center py-3">
                <div class="col-lg-6 align-self-center px-4">
                    <h2 class="fw-bold lh-1 text-uppercase" style="font-size: 6vmin">{{ text.page_1.text_section.title }}</h2>
                </div>
                <div class="col-lg-6 align-self-center px-4">
                    <p class="my-4">{{ text.page_1.text_section.text }}</p>
                    <button @click="$router.push('/two'); pageChange()" class="btn btn-outline-dark text-uppercase m-0 px-4"
                    style="border-radius: 33px;">{{ text.page_1.text_section.cta }}</button>
                </div>
            </div>
        </div>

    </div>
    </div><!-- end main container -->
</template>

<script>
import { Swiper, SwiperSlide } from 'vue-awesome-swiper'
// import axios from 'axios'
import text from '@/text.json'

export default {
    name: 'VersionOne',
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
        },
        // getData() {
        //     axios.get('https://jsonplaceholder.typicode.com/photos')
        //     .then(response => {
        //         this.data = response.data
        //         console.log(this.data)
        //     })
        //     .catch(e => {
        //         this.errors.push(e)
        //     })
        // }
    },
    created() {
        // this.getData();
    }
}
</script>

<style lang="scss" scoped>
    .swiper-slide > img {
        width: 100%;
    }

    .z--1 {
        z-index: -1;
    }
</style>