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
  --background-color: #0d0e16ff;
  --color-1: #4041b9ff;
  --color-2: #606056ff;
  --text-color: #cdcdcaff;
  --color-3: #d4d4a0ff;

}

</style>
