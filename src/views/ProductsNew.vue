<script>import axios from "axios";

export default {
  data: function () {
    return {
      message: "Welcome to Vue.js!",
      newProductParams: []
    };
  },
  created: function () { },
  methods: {
    submit: function () {
      console.log("creating something new");
      axios.post("http://localhost:3000/products", this.newProductParams).then(response => {
        console.log(response.data);
        this.$router.push("http://localhost:3000/products")
          .catch((error) => {
            this.errors = error.response.data.errors;
          });
      })
    }
  },
};
</script>

<template>
  <div class="posts-new">
    <form v-on:submit.prevent="submit()">
      <h1>New Product</h1>
      <ul>
        <li v-for="error in errors" v-bind:key="error">{{ error }}</li>
      </ul>
      <div>
        <label>Name:</label>
        <input type="text" v-model="newProductParams.input_name" />
      </div>
      <div>
        <label>Price:</label>
        <input type="text" v-model="newProductParams.input_price" />
      </div>
      <div>
        <label>Description:</label>
        <input type="text" v-model="newProductParams.input_description" />
      </div>
      <div>
        <label>In Stock:</label>
        <input type="number" v-model="newProductParams.input_in_stock" />
      </div>
      <div>
        <label>Supplier ID:</label>
        <input type="number" v-model="newProductParams.input_supplier_id" />
      </div>
      <input type="submit" value="Submit" />
    </form>
  </div>
</template>

<style>
</style>