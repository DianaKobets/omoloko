<template>
  <div v-if="isOpen" class="cart-overlay" @click="closeCart">
    <div class="cart-content" @click.stop>
      <div class="cart-header">
        <h2>Корзина</h2>
        <button class="close-btn" @click="closeCart">✕</button>
      </div>
      <div class="cart-items">
        <div v-for="(item, index) in cartItems" :key="index" class="cart-item">
          <img :src="item.image" :alt="item.title" class="thumbnail"/>
          <div class="item-info">
            <h3>{{ item.title }}</h3>
            <p>Цена: {{ item.cost }}₽</p>
            <p>Количество: {{ item.quantity }}</p>
          </div>
        </div>
      </div>
      <div class="cart-footer">
        <hr />
        <div class="cart-summary">
          <p>Всего товаров: {{ totalQuantity }}</p>
          <p>Итог: {{ totalCost }}₽</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    cartItems: Array,
    isOpen: Boolean,
  },
  computed: {
    totalQuantity() {
      return this.cartItems.reduce((acc, item) => acc + item.quantity, 0);
    },
    totalCost() {
      return this.cartItems.reduce((acc, item) => acc + item.cost * item.quantity, 0);
    }
  },
  methods: {
    closeCart() {
      this.$emit('close');
    }
  }
};
</script>

<style scoped>
.cart-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.6);
  display: flex;
  justify-content: center;
  align-items: center;
}

.cart-content {
  background: white;
  padding: 20px;
  width: 400px;
  border-radius: 10px;
  position: relative;
}

.cart-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
}

.close-btn {
  background: none;
  border: none;
  font-size: 20px;
  cursor: pointer;
}

.cart-items {
  max-height: 300px;
  overflow-y: auto;
}

.cart-item {
  display: flex;
  align-items: center;
  margin-bottom: 15px;
}

.thumbnail {
  width: 50px;
  height: 50px;
  margin-right: 15px;
}

.item-info h3 {
  font-size: 16px;
  margin: 0;
}

.cart-footer {
  margin-top: 20px;
}

.cart-summary {
  display: flex;
  justify-content: space-between;
  font-weight: bold;
}
</style>
