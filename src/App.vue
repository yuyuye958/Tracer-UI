<template>
  <router-view />
</template>

<script lang="ts">
import { ref, provide } from "vue";
import { router } from "./router";

export default {
  name: "App",
  setup() {
    const width = document.documentElement.clientWidth;
    const menuVisible = ref(width <= 667 ? false : true);
    provide("menuVisible", menuVisible);
    router.afterEach(() => {
      if (width <= 667) {
        menuVisible.value = false;
      }
    });
  },
};
</script>
