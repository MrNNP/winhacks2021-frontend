<template>
  <div id='optionbox'>
      <p>Sort By:</p>
          <select v-on:change="updateOrder($event.target.value)">
                <option value="A-Z" selected>A-Z</option>
                <option value="Z-A">Z-A</option>  
            </select> 
            <select v-on:change="updateCriteria($event.target.value)">
                <option value="municipality">Town</option>
                <option value="name" selected>Name</option>  
            </select> 
      <p>Required information</p>
        <form v-on:change="updateReqinfo($event.target.value)">
            <ul>
               <li> 
            <Input type="checkbox" value="name"></Input>Name
               </li>
               <li>
            <Input type="checkbox" value="address"></Input>Address
                </li>
                <li>
            <Input type="checkbox" value="phone"></Input>Phone Number
                </li>
                <li>
            <Input type="checkbox" value="url"></Input>Website
                </li>
            </ul>
        </form>
  </div>
</template>

<script>
export default {
    name:'optionbox',
    data(){
        return{
            order:'A-Z',
            criteria:'Name',
            minreq:['name','address','phone']
        }
    },
    methods:{
        updateOrder:function (order){
            this.order = order
            this.$emit('updateOrder',order)
        },
        updateCriteria:function (Crit){
            this.criteria = Crit
            this.$emit('updateCriteria',Crit)
        },
        updateReqinfo:function (res){
            console.log(res)
            if(this.minreq.indexOf(res) == -1){
                this.minreq.push(res);
            }else{
                this.minreq.splice(this.minreq.indexOf(res),1);
            }
            this.$emit('updateMinreq',this.minreq)
        }
    }
}
</script>

<style scoped>
#optionbox{
    min-height: 50px;
}
p{
    padding: 2px 5px;
    margin: 2px 5px;
}
</style>