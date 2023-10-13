<template>
    <!-- HTML-Template für die Komponente -->
    <div>
        <h1>{{ message }}</h1>
        <img src="'/images/'+'objectName+/.jpeg" alt="objectName">
    </div>
  </template>
  
  <script>
  export default {
    // JavaScript-Code für die Komponente
    props: {
            objectName: String,
            description: String,
            barCodeNumber: Number,
        },
    data() {
        return{
            objectName:"",
            description: "",
            barCodeNumber: 0,
        };
    },
    methods: {
      changeMessage() {
        this.message = 'Nach Klick geändert!';
      }
    }
  };
  </script>
  
  <style>
  /* CSS-Stile für die Komponente */
  </style>