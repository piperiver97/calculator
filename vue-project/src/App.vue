<script setup>
import { RouterLink, RouterView } from "vue-router";
import Header from "./components/Header.vue";
import Footer from "./components/Footer.vue";
</script>

<template>
  <body>
    <main>
      <Header></Header>

      <router-view />

      <Footer></Footer>
    </main>
  </body>
</template>
<style scoped>
main {
  background-color: rgb(168, 168, 168);
  height: 900px;
}
</style>
