<template>
  <div>
    <b-navbar toggleable="lg" type="dark" id="navbarr">
      <b-navbar-brand href="/">
        <img
          src="https://http2.mlstatic.com/storage/developers-site-cms-admin/322394706358-logo--small-v2.png"
          width="60px"
          alt
        />
        Jerónimo's Shopping
      </b-navbar-brand>
      <b-navbar-nav class="ml-auto">
        <b-nav-form>
          <b-form-input size="sm" class="mr-sm-2" placeholder="Search" v-model="value"></b-form-input>
          <b-button size="sm" class="button-anon-pen" type="submit" @click="getItem">Search</b-button>
        </b-nav-form>
      </b-navbar-nav>
    </b-navbar>

    <Items
      v-for="(item, index) in info"
      :key="index"
      :title="item.title"
      :price="item.price"
      :imgUrl="item.thumbnail"
      :sellerId="item.seller.id"
      :itemId="item.id"
      id="centered"
    ></Items>

    <div id="pag">
      <nav aria-label="Page navigation example" id="pagination">
        <ul class="pagination">
          <li class="page-item">
            <a class="page-link" v-on:click="previouspage">Previous</a>
          </li>
          <li class="page-item">
            <a class="page-link">{{page-1}}</a>
          </li>
          <li class="page-item active">
            <a class="page-link" href="#">
              {{page}}
              <span class="sr-only"></span>
            </a>
          </li>
          <li class="page-item">
            <a class="page-link">{{page+1}}</a>
          </li>
          <li class="page-item">
            <a class="page-link" v-on:click="nextpage">Next</a>
          </li>
        </ul>
      </nav>
    </div>
  </div>
</template>


<script>
import Axios from "axios";
import Items from "./Item.vue";

export default {
  name: "App",
  data() {
    return {
      info: [],
      value: null || "",
      page: 1,
      offset: 0,
    };
  },
  components: {
    Items,
  },

  props: ["object"],

  methods: {
    getItem() {
      Axios.get(
        `https://api.mercadolibre.com/sites/MCO/search?q=${this.value}&offset=${this.offset}`
      ).then((response) => {
        this.info = response.data.results;
      });
    },

    nextpage() { //Acá me falta validar que cuando llegue al límite en item.paging.total, deje de subir. 
      this.page = this.page + 1;
      this.offset = this.offset + 50;
      this.getItem();
    },

    previouspage() {
      if (this.page > 1) {
        this.offset = this.offset - 50;
        this.page = this.page - 1;
        this.getItem();
      }
    },

    //   sellerName: function(id){
    //     Axios.get(`https://api.mercadolibre.com/users/${id}`)
    //     .then(response => {
    //       this.userId=response.data.nickname
    //       console.log(this.userId)
    //     })
    //     return this.userId
    //   }
  },
};
</script>


<style>
#navbarr {
  background-color: #ffe600;
}
#centered {
  display: flex;
  margin-left: 40%;
}

#pag {
  list-style: none;
  padding-top: 30px;
  margin-left: 45%;
}
</style>