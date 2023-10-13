<template>
    <!-- HTML-Template für die Komponente -->
    <div>
        <h1>{{ message }}</h1>
        <img src="'/images/'+'objectName+/.jpeg" alt="objectName">
        <p>Beschreibung</p>
        <p>Nummer</p>
    </div>
  </template>
  
  <script>
  export default {
    // JavaScript-Code für die Komponente
   
    data() {
        return{
            objectName:"",
            description: "",
            barCodeNumber: 0,
        };
    },
    methods: {
      
    }
  };
  </script>
  
  <style>
  /* CSS-Stile für die Komponente */
  </style>