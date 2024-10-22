<template>
    <div v-if="isLoading" class="loading-indicator">
      <div class="spinner"></div>
    </div>
  
    <div v-if="!isLoading" class="products-list">
      <div class="product-card" v-for="product in products" :key="product.id">
        <img :src="product.image" :alt="product.title" />
        <div class="product-info">
          <h2>{{ product.title }}</h2>
          <div class="cost-wrapper">
            <div class="cost-not-card">
              <span class="cost">{{ product.cost }}₽</span>
              <span class="cost-info">без карты</span>
            </div>
            <div class="cost-card">
              <span class="cost">{{ product.costByCard }}₽</span>
              <span class="cost-info">по карте</span>
            </div>
          </div>
        </div>
        <button @click="addToCart(product)" class="laptop-button">Добавить в корзину</button>
        <button @click="addToCart(product)" class="mobile-button"><img src="./icons/корзина.png" alt="storage" class="card" /></button>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: 'ProductsList',
    props: {
      products: {
        type: Array,
        required: true
      },
    },
    methods: {
      addToCart(product) {
        this.$emit('add-to-cart', product);
      }
    }
  };
  </script>
  
  <style scoped>
  
  .products-list {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-evenly;
    background-color: rgb(245, 245, 245);
  }
  
  .product-card {
    height: fit-content;
    width: 25vw;
    background-color: white;
    color: rgb(32, 35, 41);
    font-size: 0.8rem;
    border-radius: 30px;
    padding: 1rem 2rem;
    margin: 10px 0px 40px 0px;
    transition: transform 0.3s ease, box-shadow 0.2s ease-in;
  }
  
  .product-card:hover {
    transform: translateY(-5px);
    box-shadow: 0px 0px 20px rgba(32, 35, 41, 0.3);
  }
  
  img {
    width: 70%;
    margin: 0 15%;
  }
  
  h2 {
    line-height: normal;
    font-weight: 600;
    overflow: hidden;
    height: 50px;
    display: -webkit-box;
    -webkit-line-clamp: 2;
    -webkit-box-orient: vertical;
  }
  
  .cost-wrapper {
    display: flex;
    flex-direction: row;
    padding: 0 10%;
  }
  
  .cost-card,
  .cost-not-card {
    display: flex;
    flex-direction: column;
    padding: 7px 10px;
    align-items: center;
  }
  
  .cost-not-card {
    color: #1e90ff;
  }
  
  .cost-card {
    color: gray;
  }
  
  .cost {
    font-weight: 700;
    font-size: 1rem;
  }
  
  span {
    font-weight: 400;
    font-size: 1rem;
  }
  
  .laptop-button {
    padding: 10px 15px;
    background-color: rgb(255, 204, 0);
    border: 2px solid transparent;
    border-radius: 30px;
    color: rgb(32, 35, 41);
    font-weight: 600;
    margin: 5% 15%;
    transition: background-color 0.2s ease-in, color 0.2s ease-in;
  }
  
  .laptop-button:hover {
    background-color: rgb(32, 35, 41);
    color: rgb(255, 204, 0);
    cursor: pointer;
  }
  
  .mobile-button {
    display: none;
  }
  
  @media (max-width: 1024px) {
    .product-card{
        margin: 20px 5px;
    }
    .laptop-button{
        width: fit-content;
        margin: 10px 15px;
        font-size: 0.8rem;
    }

     .cost-wrapper {
        padding: 0;
     }
  }
  
  @media (max-width: 768px) {
 
    .product-card{
        margin: 10px 1px;
        width: 30%;
    }
    .cost-card {
        padding: 7px 5px;
    }
    
  }
  
  @media (max-width: 426px) {

    .products-list {
      flex-direction: column;
      align-items: center;
    }
  
    .product-card {
      width: -webkit-fill-available;
      display: flex;
      flex-direction: row;
      padding: 1rem;
      margin: 0.5rem 1rem;
      height: auto;
    }
  
    .product-info {
      width:  -webkit-fill-available;
      display: flex;
      flex-direction: column;
    }
  
    img {
      width: 80px;
      margin: 0;
    }
  
    h2 {
      font-size: 14px;
      font-weight: 600;
      height: 40px;
      width: 80%;
      padding: 0px 10px;
    }
  
    .cost-card,
    .cost-not-card {
      padding-bottom: 0px;
      margin-right: auto;
      padding: 7px 1px;
    }
  
    .cost {
      font-weight: 700;
      font-size: 0.8rem;
    }
  
    span {
      font-weight: 400;
      font-size: 0.7rem;
    }
  
    .card {
      width: 15px;
    }
  
    .laptop-button {
      display: none !important;
    }
  
    .mobile-button {
      display: block;
      margin: 7% 0%;
      width: fit-content;
      height: fit-content;
      padding: 10px 13px;
      border-radius: 40px;
      border: 1px solid rgb(255, 204, 0);
      background-color: rgb(255, 204, 0);
    }
  }
  </style>
  