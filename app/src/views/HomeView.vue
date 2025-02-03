<template>
  <div>
    <h1>Brick Oven Pizza</h1>
    <div class="pizza-grid">
      <div v-for="pizza in pizzas" :key="pizza.name">
        <h2>
          <b>
            {{ pizza.name }}
          </b>
        </h2>
        <h3>${{ pizza.price }}</h3>
        <button class="pizza-btn">ADD TO CART</button><br />
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
  font-size: 60px;
}

.pizza-btn {
  background-color: #6c4f3d;
  color: white;
  font-size: 16px;
  font-weight: bold;
  padding: 10px 20px;
  border-radius: 25px;
  border: none;
  cursor: pointer;
  transition:
    background-color 0.3s ease,
    transform 0.3s ease;
  margin-bottom: 5px;
}

.pizza-btn:hover {
  background-color: #4f3a29;
  transform: translateY(-2px);
}
</style>
