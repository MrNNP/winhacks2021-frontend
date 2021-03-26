<template>
    <Navbar title="Agricultural Resources"/>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator'
import Navbar from './components/Navbar.vue'
@Component({
  components: {
    Navbar
  }
})
export default class App extends Vue {}
</script>

<style>
*{
  color: #cdcdcaff;
  background: #0d0e16ff;
  font-family: 'Open Sans', Avenir, Helvetica, Arial, sans-serif;
  margin: 0%;
  border: 0%;
  padding: 0%;
}
#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;

}

</style>
