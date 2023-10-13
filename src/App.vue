<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <header>
    <h1>The Barcode Scanner</h1>

    <div>
      <nav>
        <RouterLink to="/">Home</RouterLink>
        <!--<RouterLink to="/about">About</RouterLink>-->
      </nav>
    </div>
  </header>

  <RouterView />
</template>
