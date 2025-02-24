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
      <div class="cartContainer">
        <Cart :cart="cart" :total="total" @removeCart="removeCart" />
      </div>
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
  cart.value.push(pizza)
  total.value += pizza.price
  total.value = Math.round(total.value * 100) / 100
}

function removeCart(index) {
  if (index >= 0 && index < cart.value.length) {
    const removedPizza = cart.value[index]
    total.value -= removedPizza.price
    total.value = Math.round(total.value * 100) / 100
    cart.value.splice(index, 1)
  }
}
</script>

<style scoped>
h1 {
  text-align: center;
  font-size: 45px;
  margin-bottom: 10px;
}
.content {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: flex-start;
}
.pizza-grid {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  align-items: center;
  justify-content: space-evenly;
  width: 80%;
}
.cartContainer {
  width: 20%;
  margin-right: 20px;
}
.cart {
  padding: 20px;
  background-color: #f9f9f9;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  min-height: 1000px;
}
</style>
