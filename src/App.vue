<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <header>
    <v-toolbar>
      <v-toolbar-title>Scanner</v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn text to="/">Scanner</v-btn>
      <v-btn text to="/list">Scanned</v-btn>
    </v-toolbar>

    <div>
      <nav>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/list">List</RouterLink>
      </nav>
    </div>
  </header>

  <RouterView />
</template>
