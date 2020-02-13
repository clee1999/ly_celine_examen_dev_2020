<template>
  <div id="app">
    <Navbar></Navbar>
    <apropos></apropos>
  </div>
</template>

<script>
  import Navbar from "@/components/Navbar";
import Apropos from "@/components/apropos";
export default {
  name: 'App',
  components: {Apropos, Navbar},
}
</script>

<style>
  html {
    scroll-behavior: smooth;
  }
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;

}
</style>
