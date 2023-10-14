<template>
    <div id="product">
      <h1 id="name">{{ productObject.name }}</h1>
      <h2 id="code">{{ productObject.code }}</h2>
      <p id="description">{{ productObject.description }}</p>
      <img :src="productObject.image" id="img">
    </div>
  </template>
  
  <script>
    export default {
        props: ["productObject"],
    };
  </script>
  
  <style>
    #product{
      display: grid;
      grid-gap: 3%;
      grid-template-columns: 1fr 2fr;
      grid-template-rows: 50px 50px 100px;
      background-color: #aaaaaa;
      padding: 3%;
      margin-top: 5%;
      margin-bottom: 5%;
      margin-right: 3%;
      margin-left: 3%;
    }
    #name{
      grid-column-start: 2;
      grid-column-end: 3;
      grid-row-start: 1;
      grid-row-end: 2;

    }
    #code{
      grid-column-start: 2;
      grid-column-end: 3;
      grid-row-start: 2;
      grid-row-end: 3;
    }
    #description{
      grid-column-start: 2;
      grid-column-end: 3;
      grid-row-start: 3;
      grid-row-end: 4;
    }
    #img{
      grid-column-start: 1;
      grid-column-end: 2;
      grid-row-start: 1;
      grid-row-end: 2;
    }

  </style>