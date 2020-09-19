<template>
 <div>
  <b-navbar toggleable="lg" type="dark" id="navbarr">
    <b-navbar-brand href="/">
      <img src="https://http2.mlstatic.com/storage/developers-site-cms-admin/322394706358-logo--small-v2.png" width="60px" alt=""/>
      Jerónimo's  Shopping
    </b-navbar-brand>
    <b-navbar-nav class="ml-auto">
      <b-nav-form>
        <b-form-input size="sm" class="mr-sm-2" placeholder="Search" v-model="value"></b-form-input>
        <b-button size="sm" class="button-anon-pen" type="submit"  @click="getItem">Search</b-button>
      </b-nav-form>
    </b-navbar-nav>
  </b-navbar>
 
      <Items v-for="(item, index) in info"
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
import Axios from 'axios'
import Items from './Item.vue'

export default {
  name: 'App',
  data() {
    return {
      info:[],
      value: null || "",
      }
    },
  components:{
    Items
  },

props: ['object'],

methods:{
    getItem(e) {
        e.preventDefault();
        Axios.get(`https://api.mercadolibre.com/sites/MCO/search?q=${this.value}`)
        .then(response => {
          this.info = response.data.results;
        })
    },
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
    #navbarr{
        background-color: #FFE600;
    }

</style>