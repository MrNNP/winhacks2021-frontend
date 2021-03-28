<template>
<div id='main'>
<div v-if="apiRecived" id="arrayWrapper">  
    <div id="boxArray">
        <optionbox v-on:updateOrder="order=>{sort(order)}" v-on:updateCriteria="crit=>{sortListBy(crit)}"  v-on:updateMinreq="minreq=>{this.minreq=minreq; console.log(minreq.length)}"/>
    </div>
    <div  v-for="locat in locations" :key="locat.name+locat.address">
    <div id='boxArray' v-if="checkInfo(locat)">
        <location-infobox :Name="locat.name" :Address="locat.address" :Catagories="locat.categories" :Description="locat.description" :LocationLat="locat.position.lat" :LocationLong="locat.position.lon" :Phone="locat.phone" :Social="locat.socialMedia" :Url="locat.url"/>
    </div>
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
import optionbox from './optionbox.vue'
export default {
    name:'boxArray',
    components:{
        locationInfobox,
        optionbox
    },
    data(){
        return{
             locations:[],
             apiRecived:false,
             apiError:false,
             sortBy:'name',
             sorted:false,
             order:'A-Z',
             minreq:[]
        }
    },
    created(){
        fetch('https://winhacks2021-backend.builderpepc.repl.co/all_data',{cors:'no_cors'}).then(res=>res.json()).then(data=>{
           console.log(data.results);
            this.locations = data.results;
            
            this.apiRecived = true;
        }).catch(err=>{
            console.log(err);
            this.apiError = true;
        })
    },
    methods:{
        sort(order){
            this.order = order;
            console.log(order);
            console.log(this.sorted);
            
                this.locations = this.locations.sort((a,b)=>{
            
            if(order=='A-Z'){
                return a[this.sortBy].localeCompare(b[this.sortBy])
            }else{
                return b[this.sortBy].localeCompare(a[this.sortBy])
            }})
                this.sorted = true;
        
        },
        sortListBy(prop){
            console.log(prop);
            this.sortBy = prop.toString();
            this.sort(this.order);
        },
        checkInfo: function(inf){
           return this.minreq.every(req=>inf[req].toLowerCase()!='not found')
        }

    }
}
</script>

<style scoped>
#boxArray{
      --background-color: #E0E0E2;
  --color-1: #B5BAD0;
  --color-2: #81D2C7;
  --text-color: #001f3a;
  --color-3: #7389AE;
    background:var(--color-2);
    border-radius: 13px;
    padding: 3px 15px;
    margin: 5px;
    overflow:auto;
}
#arrayWrapper{
    display: flex;
    flex-wrap: wrap;
    justify-content: space-evenly;
}
</style> 