<template>
<div>
<div v-if="apiRecived">  
    <div class="boxArray" v-for="locat in locations" :key="locat.name">
        <location-infobox :Name="locat.name" :Address="locat.address" :Catagories="locat.categories" :Description="locat.description" :LocationLat="locat.position.lat" :LocationLong="locat.position.lon" :Phone="locat.phone" :Social="locat.socialMedia" :Url="locat.url"/>
    </div>
</div>
<div v-else-if="apiError">
<h1>An Error Occured. Please try again later</h1>
</div>
<div v-else>
<h1>Loading. Please wait</h1>
</div>
</div>
</template>

<script>
import locationInfobox from './locationInfobox.vue'
export default {
    name:'boxArray',
    components:{
        locationInfobox
    },
    data(){
        return{
             locations:[],
             apiRecived:false,
             apiError:false,
        }
    },
    created(){
        fetch('http://winhacks2021-backend.builderpepc.repl.co/all_data').then(res=>res.json()).then(data=>{
           console.log(data.results);
            this.locations = data.results;
            
            this.apiRecived = true;
        }).catch(err=>{
            console.log(err);
            this.apiError = true;
        })

    }
}
</script>

<style scoped>

</style> 