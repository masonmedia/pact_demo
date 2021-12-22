<template>
  <div id="app" class="animate__animated">
    <nav-component></nav-component>
    <!-- <transition name="slide-fade" mode="out-in"> -->
      <router-view/>
    <!-- </transition> -->
  </div>
</template>

<script>
import NavComponent from '@/components/NavComponent.vue'

export default {
  components: {
    NavComponent,
  }
}
</script>
