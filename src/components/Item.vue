<template>
<b-row class="mt-4" >
    <b-col cols="12" md="4">
        <b-card  
        img-top
        :img-src= "imgUrl"
        img-alt="Imagen relacionada a tu búsqueda"
        text-variant="black"
        :title = "title"
        >
        
        <b-card-text>
            <p>Precio: ${{price}} <br> ID del vendedor: {{seller}}</p>
        </b-card-text>
    </b-card>
    </b-col>
</b-row>

</template>
<script>
export default {
  name: "Items",
  props: {
    title: String,
    price: Number,
    imgUrl: String,
    seller: Number,
    linkSeller: String

  }
};
</script>

<style>
</style>