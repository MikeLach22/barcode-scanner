<template>
    <div>
      <h1>{{ productObject.name }}</h1>
      <h2>{{ productObject.code }}</h2>
    </div>
  </template>
  
  <script>
    export default {
        props: ["productObject"],
    };
  </script>
  
  <style>
  /* CSS-Stile für die Komponente */
  </style>