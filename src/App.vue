<template>
  <div id="app">
    <Navbar></Navbar>
    <Video></Video>
    <Texte></Texte>
    <Carte></Carte>
  </div>
</template>

<script>
import Navbar from "@/components/Navbar";
import Video from "@/components/Video";
import Texte from "@/components/Texte";
import Carte from "@/components/Carte";

export default {
  name: 'App',
  components: {
    Carte,
    Texte,
    Video,
    Navbar,
  }
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
