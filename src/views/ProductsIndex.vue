<script>
import axios from "axios";

export default {
  data: function () {
    return {
      message: "Here Are All of The Products",
      products: []
    };
  },
  created: function () {
    this.productsIndex();
  },
  methods: {
    productsIndex() {
      console.log("tryna show all the products");
      axios.get("http://localhost:3000/products.json").then(response => {
        console.log(response.data);
        this.products = response.data
      });
    }
  },
};
</script>

<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <div v-for="product in products" v-bind:key="product.id">
      {{ product }}
    </div>

  </div>
</template>

<style>
</style>