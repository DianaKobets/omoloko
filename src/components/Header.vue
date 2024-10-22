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
    padding: 0;
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
    justify-content: space-between;
    width: 80%;
    padding: 0 0 3%;
}

button{
    width: fit-content;
    height: fit-content;
    font-size: 1rem;
    padding: 0.8rem 1.5rem;
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
    margin: 0;
}

.card-count, .total-cost{
    font-weight: 600;
}

@media (max-width: 768px) {
  .title {
    font-size: 2rem;
    margin-bottom: 1.5rem;
  }

  .buttons {
    flex-direction: row;
    gap: 1.5rem;
    width: 90%;
  }

  .filter, .card {
    font-size: 0.9rem;
    padding: 0.6rem 1rem;
  }

  img {
    width: 16px;
  }
}

@media (max-width: 426px) {
  .title {
    font-size: 1.5rem;
    margin-bottom: 1rem;
  }

  .buttons {
    width: 60%;
    flex-direction: column;
    gap: 1.5rem;
    align-items: center;
  }

  .filter, .card {
    font-size: 0.8rem;
    padding: 0.5rem 0.8rem;
  }

  img {
    width: 14px;
  }
}
</style>
