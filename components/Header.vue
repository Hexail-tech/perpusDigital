<template>
  <div>
    <nav class="navbar navbar-expand-lg navbar-dark shadow fixed-top" style="background-color: #030119;">
      <div class="container">
        <a class="navbar-brand" href="#">
          <img src="~/assets/img/Logo.png" alt="" width="30" height="33"
            class="d-inline-block align-text-top left-20"></a>
        <h4 class="text-light pt-1">Perpus
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
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@500;900&display=swap');

.container {
  width: 100%;
  left: 0;
}

h4 {
  font-family: 'Poppins', sans-serif;
}
</style>
