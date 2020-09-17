<template>
    <div class="list-group">
        <Items 
        :key="item.id" 
        v-for="item in object" 
        :title="item.title" 
        :price="item.price" 
        :imgUrl="item.thumbnail" 
        :seller="item.seller.id">
        </Items>
    </div>
</template>


<script>
import Items from './Item.vue'
export default {
name: 'ListItems',
props: {
    object: []
  },
  components: {
    Items
  },
}
</script>

<style>
</style>