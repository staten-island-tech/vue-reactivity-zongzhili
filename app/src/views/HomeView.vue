<template>
  <div>
    <h1>Brick Oven Pizza</h1>
    <div class="pizza-grid">
      <PizzaCard
        v-for="pizza in pizzasArray"
        :key="pizza.name"
        :pizza="pizza"
        @add-to-Cart="addCart"
      />
    </div>
  </div>
</template>

<script setup>
import { reactive } from 'vue'
import { pizzas } from '@/assets/pizza.js'
import { cart } from '@/assets/cart.js'
import PizzaCard from '@/components/PizzaCard.vue'

const pizzasArray = reactive(pizzas)
const cartArray = reactive(cart)

function addCart(pizza) {
  console.log('Adding pizza to cart:', pizza)
  cartArray.push(pizza)
}
</script>

<style scoped>
html,
body,
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
  width: 80vh;
}
.pizza-grid {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  align-items: center;
  justify-content: space-evenly;
}
/*media queries*/
</style>
