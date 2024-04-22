<script setup>

</script>

<template>
  <nav class="navbar"  style="background-color: #e3350d;" data-bs-theme="dark">
    <div class="container">
      <router-link class="navbar-brand" to="/">
        <img src="./assets/pokeball.png" alt="Pokeball" height="26" class="d-inline-block align-text-top">
        Pokédex
      </router-link>
    </div>
  </nav>

  <main>
    <router-view></router-view>
  </main>

  <footer>
    <div> © {{ new Date().getFullYear() }}. Feito com amor por <a href="https://lutterbach.me/" style="text-decoration: none; color="white"">Alessandro Lutterbach</a>.</div>
  </footer>
</template>

<style scoped>
  body {
    background-color: #f8f8f8;
  }

  footer{
    position: fixed;
    bottom: 0;
    width: 100%;
    display: flex;
    align-items:center;
    justify-content: center;
    height: 56px;
    color: #ffffff;
    background-color: #e3350d ;
  }
</style>
