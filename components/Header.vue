<template>
  <div>
    <nav class="navbar navbar-expand-lg navbar-dark bg-primary shadow">
      <div class="container">
        <a class="navbar-brand" href="#">
          <img src="~/assets/img/Logo.png" alt="" width="30" height="33"
            class="d-inline-block align-text-top left-20"></a>
        <h4 class="text-light">Perpus
          Digital</h4>
        <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNavAltMarkup"
          aria-controls="navbarNavAltMarkup" aria-expanded="false" aria-label="Toggle navigation">
          <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarNavAltMarkup">
          <div class="navbar-nav ms-auto">
            <NuxtLink class="nav-link" aria-current="page" to="/">Home</NuxtLink>
            <NuxtLink class="nav-link" to="/pengunjung">Pengunjung</NuxtLink>
          </div>
        </div>
      </div>
    </nav>
  </div>
</template>

<script setup>

</script>

<style scoped>
.container {
  width: 100%;
  left: 0;

}
</style>
