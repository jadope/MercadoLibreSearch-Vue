<template>
  <div id="app">
    <nav class="navbar navbar-dark bg-yellow">
      <a class="navbar-brand text-dark h1" href="#">
        <img src="https://http2.mlstatic.com/storage/developers-site-cms-admin/322394706358-logo--small-v2.png" class="d-inline-block align-top" alt="">
        Jerónimo Shopping
      </a>
      <form class="form-inline">
        <input class="form-control mr-sm-2" type="search" placeholder="Search" aria-label="Search" v-model="value">
        <button class="button-anon-pen" type="submit" @click="getItem">Search</button>
      </form>
    </nav>

    <ListItems :object= 'info'/>
  </div>
</template>

<script>
import ListItems from './components/ListItems.vue'
import Axios from 'axios'

export default {
  name: 'App',
  data(){
    return{
      info: [],
      value: "cat"
    }
  },
    components: {
    ListItems
  },
  mounted () {
    Axios.get(`https://api.mercadolibre.com/sites/MCO/search?q=${this.value}`)
      .then(response => (this.info = response.data.results))
  },
  methods:{
    getItem(e) {
        e.preventDefault();
        Axios.get(`https://api.mercadolibre.com/sites/MCO/search?q=${this.value}`)
        .then(response => (this.info = response.data.results))
    }
  }

}
</script>

<style>
#app {
  background: #FFE600;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
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
