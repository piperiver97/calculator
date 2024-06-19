<script setup>
import { RouterLink, RouterView } from 'vue-router'
import Header from "./components/Header.vue";
import Footer from "./components/Footer.vue";


</script>

<template>  
<body> 
<Header></Header>
    
<main>
 <router-view />
</main>

 <Footer></Footer>

</body>
</template>

<style scoped>

body{
  background-color: rgb(202, 202, 47);
}

</style>
