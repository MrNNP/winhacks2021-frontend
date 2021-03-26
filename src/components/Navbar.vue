<template>
  <div id="topbar"><h1>{{title}}</h1></div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator'

@Component
export default class Navbar extends Vue {
  @Prop() private title!:string;
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#topbar{
  background:rgb(45, 64, 236);
  justify-content: center;
  display:flex;
  flex-wrap: wrap;
}
*{
  background: inherit;
  text-align: justify;
  text-justify:auto;
}
h1{
  padding: 1% 2% 1% 2%;
}
#box-1{
  flex: 2;
}
#box-2{
  flex: 2;
}
</style>
