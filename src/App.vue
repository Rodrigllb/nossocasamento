<template>
  <homePage></homePage>
</template>

<script>
import homePage from './components/paginaInicial.vue'

export default {
  name: 'App',
  components: {
    homePage
  }
}
</script>

<style>
* {
  padding: 0;
  margin: 0;
 
}

@font-face {
  font-family: 'RoxBoroughCF';
  src: url('./assets/fonts/roxborough-cf-medium.ttf');
}

#app {
  font-family: 'RoxBoroughCF', sans-serif, 'Courier New', Courier, monospace;
}
</style>
