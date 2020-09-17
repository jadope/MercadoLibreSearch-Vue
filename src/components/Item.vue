<template>
<<<<<<< HEAD
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

=======
    <div class="card centralizar" style="width: 18rem;">
        <img class="card-img-top" :src="imgUrl" alt="Card image cap">
        <div class="card-body">
            <h5 class="card-title">{{title}}</h5>
            <p class="card-text">El precio es: ${{price}}</p>
        </div>
    </div>
>>>>>>> b0376dc41af5a6087358bdaccd4c3534c16fab00
</template>
<script>
export default {
  name: "Items",
  props: {
    title: String,
    price: Number,
<<<<<<< HEAD
    imgUrl: String,
    seller: Number,
    linkSeller: String

=======
    imgUrl: String
>>>>>>> b0376dc41af5a6087358bdaccd4c3534c16fab00
  }
};
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