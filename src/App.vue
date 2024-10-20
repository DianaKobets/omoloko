<template>
  <div id="app">
    <div class="content">
      <Header></Header>
      <ProductsList :products="products"/>
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
      products:[],

    };
  },
  methods:{
    fetchProducts(){
      axios.get('https://webapi.omoloko.ru/api/v1/products')
      .then(response =>{
        this.products = response.data.products;
      })
      .catch(error =>{
        console.log(error);
      });
    }
  },
  created() {
    this.fetchProducts();
  },
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
