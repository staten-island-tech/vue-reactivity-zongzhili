<template>
  <div>
    <h1>Brick Oven Pizza</h1>
    <div class="pizza-grid">
      <PizzaCard v-for="pizza in pizzasArray" :key="pizza.name" :pizza="pizza" />
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import { pizzas } from '@/assets/pizza.js'
import PizzaCard from '@/components/PizzaCard.vue'

const pizzasArray = ref(pizzas)
</script>

<style scoped>
html,
body,
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
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
