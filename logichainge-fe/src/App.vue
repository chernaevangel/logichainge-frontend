<script setup>
import HelloWorld from './components/HelloWorld.vue'
</script>

<template>
  <div id="app">

      <!-- <img alt="Vue logo" class="logo" src="@/assets/logo.svg" width="125" height="125" /> -->

      <div class="wrapper">
        <!-- <HelloWorld msg="You did it!" /> -->

        

        
        <nav>
          <router-link to="/">Home</router-link>
          <router-link to="/about">Metrics</router-link>
        </nav>
      </div>

      <div id="content-wrapper">
         <router-view />
     </div>
  </div>
</template>

<style scoped>

  #app {
    height: 100vh;
    width: 100% ;
    background-color: rgb(255, 255, 255);
 }

 .wrapper{
  background-color: rgb(251, 251, 251);
 }


 #content-wrapper{
  height: 100%;
  width: 100%;
  display: flex;
 }





</style>
