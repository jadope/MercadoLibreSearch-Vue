<template>
  <div id="app">
    <b-navbar toggleable="lg" type="dark" variant="warning">
      <b-navbar-brand href="#">
        <img src="https://http2.mlstatic.com/storage/developers-site-cms-admin/322394706358-logo--small-v2.png" width="60px" alt=""/>
        Jerónimo Shopping
      </b-navbar-brand>
      <b-navbar-nav class="ml-auto">
        <b-nav-form>
          <b-form-input size="sm" class="mr-sm-2" placeholder="Search" v-model="value"></b-form-input>
          <b-button size="sm" class="button-anon-pen" type="submit"  @click="getItem">Search</b-button>
        </b-nav-form>
      </b-navbar-nav>
    </b-navbar>
    <ListItems :object= 'info' :method="nombrevendedor" />

  <router-view/>

  </div>
</template>

<script>
import Axios from 'axios'
import ListItems from './components/ListItems.vue'

export default {
  name: 'App',
  data() {
    return {
      info:[],
      value:""
    }

  },
  components: {
    ListItems
      },
  methods:{
    getItem(e) {
        e.preventDefault();
        Axios.get(`https://api.mercadolibre.com/sites/MCO/search?q=${this.value}`)
        .then(response => (this.info = response.data.results))
    },

    nombrevendedor: function(identificacion){
      this.$http
      .get(`https://api.mercadolibre.com/users/${identificacion}`)
      .then(resp => {
        this.usuarioid=resp.body['nickname'];
        this.nombrev[0]=this.usuarioid;        
      })
      return  this.nombrev[0].toString()
    }
  }
}
</script>

<style>
#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  text-align: center;
  margin-top: 0px;
}
.button-anon-pen{
      margin: 15px;
    padding: 0;

    text-align: center;
    position: relative;
    background-image: linear-gradient(115deg,#4fcf70,#fad648,#a767e5,#12bcfe,#44ce7b);
    border-radius: 6px;
    box-sizing: border-box;
    color: #fff;
    display: inline-block;
    z-index: 2;
}

.button-anon-pen span {
  padding: 10px 25px;
    font-size: 1.1rem;
    align-items: center;
    background: #000;
    border-radius: 3px;
    display: block;
    justify-content: center;
    margin: 3px;
    box-sizing: border-box;
    height: 100%;
     transition: background .5s ease;
}

.button-anon-pen:hover{
      animation: Sidebar_rainbowBorder-2QRx- .5s linear infinite;
  -webkit-animation: Sidebar_rainbowBorder-2QRx- .5s linear infinite;
}

@-webkit-keyframes Sidebar_rainbowBorder-2QRx- {
	0%,
	to {
		background-image: linear-gradient(115deg, #4fcf70, #fad648, #a767e5, #12bcfe)
	}
	25% {
		background-image: linear-gradient(115deg, #fad648, #a767e5, #12bcfe, #4fcf70)
	}
	50% {
		background-image: linear-gradient(115deg, #a767e5, #12bcfe, #4fcf70, #fad648)
	}
	75% {
		background-image: linear-gradient(115deg, #12bcfe, #4fcf70, #fad648, #a767e5)
	}
}

@keyframes Sidebar_rainbowBorder-2QRx- {
	0%,
	to {
		background-image: linear-gradient(115deg, #4fcf70, #fad648, #a767e5, #12bcfe)
	}
	25% {
		background-image: linear-gradient(115deg, #fad648, #a767e5, #12bcfe, #4fcf70)
	}
	50% {
		background-image: linear-gradient(115deg, #a767e5, #12bcfe, #4fcf70, #fad648)
	}
	75% {
		background-image: linear-gradient(115deg, #12bcfe, #4fcf70, #fad648, #a767e5)
	}
}


</style>
