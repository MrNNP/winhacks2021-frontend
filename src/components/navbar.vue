<template>
  <div id='navbar'><img src='wheat.png'><div id="title"><h1>{{title}}</h1></div><img src='wheat.png'></div>
</template>

<script>
export default {
    name:'navbar',
    props:['title']
}
</script>

<style scoped>
#navbar{
  display:flex;
  justify-content: space-evenly;
}
#title{
padding: 5px 15px;
font-weight:bolder;
}
</style>