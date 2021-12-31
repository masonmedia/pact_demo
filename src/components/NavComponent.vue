<template>
    <nav class="navbar navbar-dark fixed-top p-3"
    :class="versionOne ? '' : 'bg-dark'"
    :style="versionOne ? 'background: #2C2C2C;' : 'bg-dark'">
        <div class="container-fluid">
            <router-link class="navbar-brand text-lowercase" :to="$router.options.routes[0]">{{ text.site_brand }}</router-link>
            <button class="navbar-toggler border-0 px-0 px-md-2" type="button" data-bs-toggle="offcanvas" data-bs-target="#offcanvasNavbar"
                aria-controls="offcanvasNavbar">
                <svg xmlns="http://www.w3.org/2000/svg" width="36" height="36" fill="currentColor" class="bi bi-three-dots-vertical" viewBox="0 0 16 16">
                    <path d="M9.5 13a1.5 1.5 0 1 1-3 0 1.5 1.5 0 0 1 3 0zm0-5a1.5 1.5 0 1 1-3 0 1.5 1.5 0 0 1 3 0zm0-5a1.5 1.5 0 1 1-3 0 1.5 1.5 0 0 1 3 0z"/>
                </svg>
            </button>
            <div class="offcanvas offcanvas-end bg-dark text-light" tabindex="-1" id="offcanvasNavbar"
                aria-labelledby="offcanvasNavbarLabel">
                <div class="offcanvas-header">
                    <button type="button" class="btn-close d-flex ms-auto btn-lg" data-bs-dismiss="offcanvas"
                    aria-label="Close">
                        <svg xmlns="http://www.w3.org/2000/svg" width="26" height="26" fill="currentColor" class="bi bi-x-lg text-light" viewBox="0 0 16 16">
                            <path fill-rule="evenodd" d="M13.854 2.146a.5.5 0 0 1 0 .708l-11 11a.5.5 0 0 1-.708-.708l11-11a.5.5 0 0 1 .708 0Z"/>
                            <path fill-rule="evenodd" d="M2.146 2.146a.5.5 0 0 0 0 .708l11 11a.5.5 0 0 0 .708-.708l-11-11a.5.5 0 0 0-.708 0Z"/>
                        </svg>
                    </button>
                </div>
                <div class="offcanvas-body p-4">
                    <ul class="navbar-nav justify-content-end align-items-start h-100 flex-grow-1 pe-3 py-5">
                        <li class="text-lowercase text-light mb-2">{{ text.site_brand }}</li>
                        <router-link 
                        v-for="route in $router.options.routes" :key="route.path"
                        :to="route.path" 
                        class="fs-3 lh-base fw-bold text-uppercase text-decoration-none">
                            <li data-bs-dismiss="offcanvas" aria-label="Close"
                            v-html="route.name"></li>
                        </router-link>
                    </ul>
                </div>
            </div>
        </div>
    </nav>
</template>

<style scoped>

.navbar-toggler:focus {
    text-decoration: none;
    outline: 0;
    box-shadow: none;
}


/* button outline remove */

input[type=button], 
input[type=button]:focus {
  outline: none;
}

</style>
<script>
import text from '@/text.json'
export default {
    name: 'NavComponent',
    data() {
        return {
            text: text,
            isActive: false,
        }
    },
    computed: {
        versionOne() {
            return this.$route.name == 'One' ? true : false
        }
    },
    methods: {
        navToggle() {
            this.isActive = !this.isActive;
        },
    },
}
</script>