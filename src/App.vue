<template>
  <div id="app" class="animate__animated animate__fadeIn">
    <nav-component></nav-component>
    <!-- <transition name="fade" mode="out-in"> -->
      <router-view/>
    <!-- </transition> -->
  </div>
</template>

<script>
import NavComponent from '@/components/NavComponent.vue'

export default {
  components: {
    NavComponent,
  },
  data() {
    return {}
  },
}
</script>
