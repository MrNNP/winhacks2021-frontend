<template>
  <div id="app">
    <navbar title="WINFARMS"/>
    <box-array />
  </div>
</template>

<script>
import boxArray from './components/boxArray.vue'
import navbar from './components/navbar.vue'
export default {
  name: 'App',
  components: {
    navbar,
    boxArray
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
    background-color:var(--background-color);
    color: var(--text-color);
}
body{
  background: var(--background-color);
}
*{
  --background-color: #E0E0E2;
  --color-1: #B5BAD0;
  --color-2: #81D2C7;
  --text-color: #001f3a;
  --color-3: #7389AE;

}

</style>
