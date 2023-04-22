<template>
  <div class="home">
    <Navbar msg="TesCode" />
    <div class="container">
      <Hero />
    
      <div class="row mt-3">
        <div class="col">
          <div class="input-group mb-3">
            
            <input
              v-model="search"
              type="text"
              class="form-control"
              placeholder="Cari Makanan Kesukaan Anda .."
              aria-label="Cari"
              aria-describedby="basic-addon1"
              @keyup="searchProduct"
            />

            <div class="input-group-prepend">
              <span class="input-group-text" id="basic-addon1">
                <b-icon-search></b-icon-search>
              </span>
            </div>
          </div>
        </div>
      </div>
      <div class="row mb-3">
        <div class="col-md-3 mt-3" v-for="product in products" :key="product.id">
          <CardProduct :product="product" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  // @ is an alias to /src
  import Navbar from "@/components/Navbar.vue";
  import CardProduct from "@/components/CardProduct.vue";
  import axios from "axios";

  import Hero from "@/components/Hero.vue";
  export default {
    name: "HomeView",
    components: {
      Navbar,
      Hero,
      CardProduct,
    },
    data() {
      return {
        products: [], 
        search :'',
      };
    },
    methods: {
      setProduct(data) {
        this.products = data;
      },
      searchProduct(){
        axios
        .get("http://api.tvmaze.com/search/shows?q=girls"+this.search)
        .then((response) => this.setProduct(response.data))
        .catch((error) => console.log(error));
      }
    },
    mounted() {
      axios
        .get("http://api.tvmaze.com/search/shows?q=girls")
        .then((response) => {this.setProduct(response.data)})
        .catch((error) => console.log(error))
    },
  };
</script>