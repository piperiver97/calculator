<template>
  <header class="d-flex justify-content-center py-3 mb-8 border-bottom">
    <ul class="nav nav-pills">
      <li class="nav-item">
        <router-link to="/"><a href="#" class="nav-link">Calculator</a></router-link>
      </li>
      <li class="nav-item">
        <router-link to="/converter"><a href="#" class="nav-link">Converter</a></router-link>
      </li>
      <li class="nav-item">
        <router-link to="/weather"><a href="#" class="nav-link">Weather</a></router-link>
      </li>
    </ul>
  </header>
</template>

<style scoped>

header {
  background-color: rgb(66, 66, 66);;
  padding: 10px;
}

.nav {
  display: flex;
  justify-content: space-between;
  padding: 0;
}

.nav-item {
  background-color: #4bade2;
  list-style: none !important;
  margin: 0 10px;
  border-radius: 10px;
}

.nav-item:hover {
  color: #fff;
  background-color: #93ddff;
  border-color: #93ddff;
  border-radius: 10px;
}

.nav-link {
  color: rgb(255, 255, 255);
  text-decoration: none; 
  padding: 10px 15px;
}

.nav-link:hover {
  color: #fff;
  background-color: #93ddff;
  border-color: #93ddff;
  border-radius: 10px;
}
</style>
