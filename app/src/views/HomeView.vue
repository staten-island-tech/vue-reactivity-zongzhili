<template>
  <div class="homeContainer">
    <h1>Brick Oven Pizza</h1>
    <div class="content">
      <div class="pizza-grid">
        <PizzaCard
          v-for="pizza in pizzasArray"
          :key="pizza.name"
          :pizza="pizza"
          @addToCart="addToCart"
        />
      </div>
      <Cart :cart="cart" :total="total" />
    </div>
  </div>
</template>

<script setup>
import { reactive, ref } from 'vue'
import { pizzas } from '@/assets/pizza.js'
import { cart } from '@/assets/cart.js'
import Cart from '@/views/Cart.vue'
import PizzaCard from '@/components/PizzaCard.vue'

const pizzasArray = reactive(pizzas)
const total = ref(0)

function addToCart(pizza) {
  console.log('Adding to cart:', pizza.name)

  cart.value.push(pizza)
  total.value += pizza.price
  total.value = Math.round(total.value * 100) / 100

  console.log('Updated total:', total.value)
}
</script>

<style scoped>
body {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
.content-container {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  gap: 20px;
}
.pizza-grid {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  align-items: center;
  justify-content: space-evenly;
}
.cart {
  flex: 1;
  padding: 20px;
  border: 1px solid #ddd;
  background-color: #f9f9f9;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

/*media queries*/
</style>
