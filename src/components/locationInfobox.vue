<template>
  <div class="locationProperies">
      <ul>
          <li id="name" v-if="Name"><strong>{{Name}}</strong></li>
          <li v-if="LocationLat && LocationLong">Coordinates: {{LocationLat}}, {{LocationLong}}</li>
          <li v-if="Description">Description: {{Description}}</li>
          <li v-if="Address">Address:{{Address}}</li>
          <li v-if="Phone">Phone number:{{Phone}}</li>
          <li v-if="Url!='Not found'"><a :href="`//${Url}`" target="_blank" rel="noopener noreferrer">Link</a></li>
          <li v-if="Catagories">Catagories: {{Catagories.join(', ')}}</li>
          <li v-if="Social">Social: {{Social}}</li>
      </ul>
  </div>
</template>

<script>
export default {
    name:'locationInfobox',
    props:['Name','LocationLat','LocationLong','Description',"Address","Phone","Url","Catagories","Social"],
    
}
</script>

<style scoped>
#name{
    list-style-type: none;
    justify-content: center;
}
</style>