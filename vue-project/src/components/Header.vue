<template>
  <header class="d-flex justify-content-center py-3 mb-8 border-bottom">
      <ul class="nav nav-pills">
          <li class="nav-item">
              <router-link to="/"><a href="#" class="nav-link" aria-current="page">Calculator</a></router-link>
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
  background-color: #93DDFF;
  padding: 10px; 
  
}

.nav {
  
  display: flex; 
  justify-content: space-between;
  padding: 0; 
}

.nav-item {
  background-color: #027DC4;
  list-style: none; 
  margin: 0 10px; 
  border-radius: 10px;
}

.nav-link {
  color: aliceblue;
  text-decoration: none; 
  padding: 10px 15px; 
}
</style>
