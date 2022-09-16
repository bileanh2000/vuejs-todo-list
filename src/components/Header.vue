<template>
  <header>
    <div class="wrapper">
      <div class="logo">TodoList</div>
      <nav class="navbar">
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/about">Task was done</RouterLink>
      </nav>
    </div>
  </header>
</template>

<script>
import { RouterLink, RouterView } from "vue-router";

export default {
  name: "Header",
};
</script>

<style scoped>
header {
  background-color: #3d8361;
  color: white;
  position:sticky;
  top:0;
  z-index: 99;
}
.wrapper {
  max-width: 1250px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin: 0 auto;
  padding: 9px;
}
.logo {
  font-weight: bold;
  text-transform: uppercase;
  font-size: 1.2rem;
}
a {
  height: 100%;
  padding: 10px;
}
@media (hover: hover) {
  a:hover {
    background-color: hsla(160, 100%, 37%, 0.2);
  }
}
</style>
