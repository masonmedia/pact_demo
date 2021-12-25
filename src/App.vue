<template>
  <div id="app" class="animate__animated animate__fadeIn">
    <nav-component></nav-component>
    <!-- <transition name="slide-fade" mode="out-in"> -->
      <!-- <transition mode="out-in" name="custom" 
      enter-active-class="animate__animated animate__fadeIn" 
      leave-active-class="animate__animated animate__fadeOut"
      > -->
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
  }
}
</script>
