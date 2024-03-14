<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>
<template>
  <header>
    <div class="wrapper">
      <nav class="navbar navbar-expand-lg bg-body-tertiary">
        <div class="container-fluid">
          <RouterLink class="navbar-brand" to="/">Navbar</RouterLink>
          <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNavAltMarkup"
            aria-controls="navbarNavAltMarkup" aria-expanded="false" aria-label="Toggle navigation">
            <span class="navbar-toggler-icon"></span>
          </button>
          <div class="collapse navbar-collapse" id="navbarNavAltMarkup">
            <div class="navbar-nav">
              <RouterLink class="nav-link active"  to="/">Home</RouterLink>
              <RouterLink class="nav-link active"  to="/about">about us</RouterLink>
              <RouterLink class="nav-link active"  to="/student">student </RouterLink>
              <!-- <RouterLink class="nav-link active"  to="/home">contact us</RouterLink> -->
              
            </div>
          </div>
        </div>
      </nav>
    </div>
  </header>
  <RouterView />
</template>
