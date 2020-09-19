<template>
    <div class="list-group">
        <Items v-for="(item, index) in object"
        :key="index"  
        :title="item.title" 
        :price="item.price" 
        :imgUrl="item.thumbnail"
        :sellerId="item.seller.id"
        :itemId="item.id">
        

        </Items>
    </div>
</template>




<script>

//import Axios from 'axios'
import Items from './Item.vue'
export default {
  name: 'ListItems',
  props: ['object'],
  components: {
    Items
  },
   methods:{

     getItemDetail(){

     }
  //   sellerName: function(id){
  //     Axios.get(`https://api.mercadolibre.com/users/${id}`)
  //     .then(response => {
  //       this.userId=response.data.nickname
  //       console.log(this.userId)        
  //     })
  //     return this.userId
  //   }
   }  
}
</script>

<style>
</style>