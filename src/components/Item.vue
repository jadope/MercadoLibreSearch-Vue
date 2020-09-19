<template>
<b-row class="mt-4" >
    <b-col cols="12" md="4">
        <b-card  
        img-top
        :img-src= "imgUrl"
        text-variant="black"
        :title = "title"
        >
        
        <b-card-text>
            <p>Precio: ${{price}} <br> La ID del vendedor es: {{sellerId}} </p>
        </b-card-text>
    </b-card>
    </b-col>
</b-row>
</template>

<script>
export default {
  name: "Item",
  props: {
    title: String,
    price: Number,
    imgUrl: String,
    sellerId: Number
  }
};
</script>

<style>
</style>