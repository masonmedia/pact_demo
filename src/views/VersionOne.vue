<template>
    <div id="one" class="container-fluid position-relative px-0">
        <!-- swiper layer -->
        <div class="animate__animated animate__slideOutRight h-100 w-100 position-absolute start-0"
        style="background: #000; z-index: 1000;"></div>
        <!-- banner -->
        <div class="container-fluid py-5" style="background: #2C2C2C;">
            <div class="row p-5">
                <div class="col-lg-12 py-5 px-0">
                    <h1 class="fw-bold text-uppercase lh-1 animate__animated animate__fadeIn"
                    style="font-size: 8vmin; color: #FFFAF340;">
                    <span class="px-0 px-md-5" style="text-indent: 50px;"></span>{{ text.page_1.page_title }}
                    </h1>
                </div>
            </div>
            <div class="row">
                <!-- carousel vertical title -->
                <div class="rotate-90 col-md-2 d-none d-md-flex justify-content-center align-items-center text-center"
                :class="isActive ? 'position-absolute z--1' : ''" style="color: #FFFAF3;">
                    <p style="font-size: 16px"  v-html="text.page_1.carousel_title"></p>
                </div>
                <!-- carousel -->
                <div :class="isActive ? 'col-md-12' : 'col-md-10'"
                class="d-flex justify-content-center align-items-center text-center">
                    <swiper class="swiper" 
                    ref="mySwiper"
                    :options="swiperOption" 
                    @slideChangeTransitionStart="slideStart">
                        <button :class="isActive ? 'puff-out-center' : ''"
                        class="btn btn-sm btn-light d-flex justify-content-center align-items-center position-absolute start-50 translate-middle shadow text-uppercase"
                        style="width: 50px; height: 50px; top: 25%; border-radius: 100%; z-index: 10; font-size: 10px">
                            {{ text.carousel_drag }}
                        </button>
                        <swiper-slide v-for="(slide, index) in text.page_2.carousel_slides" :key="index">
                            <!-- slide -->
                            <div class="card" style="background: #2C2C2C;">
                                <img :src="require(`@/${slide.img}`)" class="card-img-top"
                                style="border-radius: 33px 33px 33px 0;">
                                <div class="card-body text-light text-start py-4"
                                style="border-radius: 0 0 33px 0; background: #2C2C2C;">
                                    <p class="lh-sm text-light text-uppercase" style="font-size: 12px">Category</p>
                                    <p class="small lh-sm fw-light text-light pe-2">{{ slide.text }}</p>
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
                        <h2 class="fw-bold lh-1 text-uppercase" style="font-size: 6vmin">
                        {{ text.page_1.text_section.title }}</h2>
                    </div>
                    <div class="col-lg-6 align-self-center px-4">
                        <p class="my-4">{{ text.page_1.text_section.text }}</p>
                        <button @click="$router.push({ path: 'two' })"
                        class="btn btn-sm btn-outline-dark rounded-pill text-uppercase m-0 px-4">{{ text.page_1.text_section.cta }}</button>
                    </div>
                </div>
            </div>

        </div>
    </div><!-- end main container -->
</template>

<script>
    import { Swiper, SwiperSlide } from 'vue-awesome-swiper'
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
        computed: {
            swiper() {
                return this.$refs.mySwiper.$swiper
            }
        },
        methods: {
            slideStart() {
                console.log("slide started")
                this.isActive = true
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
        mounted() {
            console.log('Current Swiper instance object', this.swiper)
            this.swiper.slideTo(0, 1000, false)
        }
    }
</script>

<style lang="scss" scoped>
    h1 {
        font-size: 76px;
    }
    .swiper-slide>img {
        width: 100%;
    }

    .z--1 {
        z-index: -1;
    }

    @media(max-width: 768px) {
        h1 {
            font-size: 8vmin;
        }
    }
</style>