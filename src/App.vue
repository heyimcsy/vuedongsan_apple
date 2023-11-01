<template>
  <div class="menu">
    <a v-for="(menuName,i) in menu" :key="i">{{menuName}}</a>
  </div>
  </template>
  <script>
  export default {
    name:'App',
    data() {
      return{
        menu:['Home','Shop','About']
      }
    }
  }
  </script>
  
  <style>
  body {
    margin :0
  }
  div {
    box-sizing: border-box;
  }
  .menu {
    background: darkslateblue;
    padding: 15px;
    border-radius: 5px;
  }
  .menu a {
    color: white;
    padding: 10px;
  }
  </style>