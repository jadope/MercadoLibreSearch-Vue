<template>
<<<<<<< HEAD
    <div class="list-group">
        <Items 
        :key="item.id" 
        v-for="item in object" 
        :title="item.title" 
        :price="item.price" 
        :imgUrl="item.thumbnail" 
        :seller="item.seller.id">
        </Items>
=======
    <div  class="list-group">
        <ul class="list-group-item">
            <li><Items :key="obj" v-for="obj in object" :title="obj.title" :price="obj.price" :imgUrl="obj.thumbnail"></Items> </li>        
        </ul>
>>>>>>> b0376dc41af5a6087358bdaccd4c3534c16fab00
    </div>
</template>


<script>
import Items from './Item.vue'
export default {
<<<<<<< HEAD
name: 'ListItems',
=======
name: 'ItemsList',
>>>>>>> b0376dc41af5a6087358bdaccd4c3534c16fab00
props: {
    object: []
  },
  components: {
    Items
  },
}
</script>

<style>
<<<<<<< HEAD

=======
    .centralizar{
        display: block;
    margin-left: auto;
    margin-right: auto
    }
>>>>>>> b0376dc41af5a6087358bdaccd4c3534c16fab00
</style>