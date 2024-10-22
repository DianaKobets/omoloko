<template>
  <div id="app">
    <div class="content">
      <Header 
        :cartCount="cartCount" 
        :totalCost="totalCost"
        @sortProducts="sortProductsAlphabetically"
      />
      <ProductsList :products="products" @add-to-cart="addToCart"/>
    </div>
    <footer class="footer">
      Created by Diana Kobets
    </footer>
  </div>
</template>

<script>
import axios from 'axios';
import Header from './components/Header.vue';
import ProductsList from './components/ProductsList.vue';

export default {
  name: 'App',
  components: {
    Header,
    ProductsList
  },
  data(){
    return{
      products: [],
      cartCount: 0,
      totalCost: 0,
      isLoading: true,
    };
  },
  methods:{
    fetchProducts(){
      this.isLoading = true;
      axios.get('https://webapi.omoloko.ru/api/v1/products')
      .then(response =>{
        this.products = response.data.products.slice(0,10);
      })
      .catch(error =>{
        console.log(error);
      })
      .finally(() => {
        this.isLoading = false;  
      });
    },
    addToCart(product){
      this.cartCount += 1;
      this.totalCost += product.cost;
    },
    sortProductsAlphabetically(){
      this.products.sort((a,b) => a.title.localeCompare(b.title));
    }
  },
  created() {
    this.fetchProducts();
  }
};
</script>

<style scoped>
.footer {
  background-color: rgb(32, 35, 41);
  color: #9e9e9e;
  font-weight: bold;
  padding: 10px;
  text-align: center;
  position: relative;
  bottom: 0;
  width: 100%;
}
</style>
