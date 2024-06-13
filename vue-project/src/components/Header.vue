<template>
    <header class="d-flex flex-wrap justify-content-center py-3 mb-4 border-bottom">
      <a href="/" class="d-flex align-items-center mb-3 mb-md-0 me-md-auto link-body-emphasis text-decoration-none">
        <svg class="bi me-2" width="40" height="32"><use xlink:href="#bootstrap"></use></svg>
        
      </a>

      <ul class="nav nav-pills">
        <li class="nav-item">
            <RouterLink to="/"><a href="#" class="nav-link active" aria-current="page">Calculator</a></RouterLink></li>
        <li class="nav-item">
            <router-link to="/converter"><a href="#" class="nav-link">Converter</a></router-link></li>
        <li class="nav-item">
          <router-link to="/weather"><a href="#" class="nav-link">Weather</a></router-link></li>
        
      </ul>
    </header>
    </template>