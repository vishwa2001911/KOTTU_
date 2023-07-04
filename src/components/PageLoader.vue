<template>
    <div class="page-loader" v-if="!isloaded" >
      <img style="width: 150px;" src="https://github.com/vishwa2001911/Project_/blob/master/img/Yellow%20Abstract%20Cooking%20Fire%20Free%20Logo%20(1).png?raw=true" alt="">
    </div> 
  </template>
  
  <script>
    export default {
      data: () => {
        return {
          isloaded: false
        }
      },
      methods:{
        time(){
            this.isloaded = true
        }
      },
      mounted() {
        document.onreadystatechange = () => {
          window.setTimeout(this.time, 5000); 
          if (document.readyState == "complete") { 
            this.isloaded = true
          } 
        }
      },
    }
  </script>
  
  <style>

.page-loader {
      display: flex;
      justify-content: center;
      align-items: center;
      position: fixed;
      top: 0;
      left: 0;
      width: 100vw;
      height: 100vh;
      background-color: black;
      z-index: 999;
    }

  </style>