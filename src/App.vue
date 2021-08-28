<template>
  <router-view></router-view>
</template>

<script lang="ts">
import { provide, ref } from "vue";
import { router } from './router';
export default {
  name: 'App',
  setup() {
    const menuVisible = ref(true);
    let width;
    window.addEventListener('resize', (e) => {
      width = document.documentElement.clientWidth
      if (width > 500) {
        menuVisible.value = true;
      }
    })
    provide('menuVisible', menuVisible);
    router.afterEach(() => {
      if (width <= 500) {
        menuVisible.value = false;
      }
    })
  }
}
</script>
