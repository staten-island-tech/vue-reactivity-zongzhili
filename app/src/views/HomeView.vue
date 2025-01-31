<template>
  <div>
    <h1>Fresh Pizza</h1>
    <div class="pizza-grid">
      <div v-for="pizza in pizzas" :key="pizza.name">
        <ul>
          {{
            pizza.name
          }}
          - ${{
            pizza.price
          }}
        </ul>
        <img :src="pizza.image" alt="Pizza image" class="pizza-image" />
      </div>
    </div>
  </div>
</template>

<script setup>
import { reactive } from 'vue'
import { pizzas } from '@/assets/array.js'

const pizzasArray = reactive(pizzas)
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
  justify-content: center;
  gap: 10px;
}
.pizza-image {
  width: 400px;
  height: 400px;
  object-fit: cover;
}
h1 {
  text-align: center;
}
</style>
