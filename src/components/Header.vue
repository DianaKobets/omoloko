<template>
  <div class="title-container">
    <h1 class="title">IceCream Store</h1>

    <div class="buttons">
      <button @click="$emit('sortProducts')" class="filter">Фильтровать по названию</button>
      <button class="card">
        <img src="./icons/корзина.png" alt="storage">
        <span v-if="cartCount" class="card-count">({{ cartCount }})</span> 
        <span v-if="totalCost" class="total-cost"> - {{ totalCost }}₽</span>
      </button>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    cartCount: {
      type: Number,
      default: 0
    },
    totalCost: {
      type: Number,
      default: 0
    }
  }
};
</script>

<style scoped>
div{
    background-color: rgb(245, 245, 245);
}

.title-container{
    width: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
    text-align: center;
    justify-content: center;
    background-size: cover;
    padding: 0px 0px 30px 0px;
}

.title{
    color: rgb(32, 35, 41);
    font-weight: 900;
    font-size: 3em;
    border-bottom: 3px solid rgb(255, 204, 0);
    margin-bottom: 2rem;
}

.buttons{
    display: flex;
    gap: 48rem;
    padding: 0 0 3rem 2rem;
}

button{
    width: fit-content;
    height: fit-content;
    font-size: 1rem;
    padding: 0.8rem 1.5rem;
    position: absolute;
    background-color: rgb(255, 204, 0);
    border: 2px solid transparent;
    border-radius: 30px;
    color:rgb(32, 35, 41);
    font-weight: 600;
    gap: 7px;
    display: flex;
    align-items: center;
    transition: transform .3s ease;
}

button:hover{
    transform: translateY(-3px);
    cursor: pointer;
}

img{
    width: 18px;
    margin: 1px 0 0 -1px;
}

.filter{
    left: 6rem; 
}

.card{
    right: 6rem; 
}

.total-card{
    display: flex;
    flex-direction: row;
    font-size: 0.8rem;
    background-color: rgb(255, 204, 0);
    gap:7px;
    align-items: center;
}

.card-count, .total-cost{
    font-weight: 600;
}

@media (max-width:426px) {
  
  .filter{
    left: 2rem; 
    font-size: 0.8rem;
    padding: 10px 10px;
}

.card{
    right: 2.5rem; 
    font-size: 0.8rem;
    padding: 8px 15px;
}

}
</style>