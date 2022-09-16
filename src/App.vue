<script>
import { RouterLink, RouterView } from "vue-router";
import HelloWorld from "./components/HelloWorld.vue";
import HeaderVue from "./components/Header.vue";
export default {
  name: "App",
  components: { HeaderVue },
};
</script>

<template>
  <HeaderVue />
  <main class="main-content">
    <RouterView />
  </main>
</template>

<style scoped>
.main-content {
  margin-top: 20px;
}
</style>
