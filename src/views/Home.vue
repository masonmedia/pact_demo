<template>
  <div class="container-fluid bg-dark position-relative">
    <div class="animate__animated animate__slideOutRight h-100 w-100 position-absolute start-0"
    style="background: #000; z-index: 1000;"></div>
    <div class="row min-vh-100 justfy-content-start align-items-center">
      <div class="col-lg-10 p-5 text-focus-in">
        <h6 class="mb-4" style="color: lightgrey">{{ text.project_title }}</h6>
        <h1 class="fw-bold text-uppercase lh-1" style="font-size: 7vmin; color: #FFFAF340;"
          v-html="text.home_page.page_title"></h1>
        <button @click="$router.push({ path: 'one' })" class="btn btn-outline-light mt-2">next</button>
      </div>
    </div>
  </div>
</template>

<script>
  import text from '@/text.json'

  export default {
    name: 'Home',
    data() {
      return {
        text: text
      }
    },
  }
</script>