<template>
  <div class="card">
    <img :src="pizza.image" alt="Pizza image" class="pizza-image" />
    <h2>
      {{ pizza.name }}
    </h2>
    <h3>${{ pizza.price }}</h3>
    <button class="pizza-btn" @click="addToCart">Add to Cart</button>
  </div>
</template>

<script setup>
const props = defineProps({
  pizza: Object,
})

const emit = defineEmits(['addToCart'])

function addToCart() {
  emit('addToCart', props.pizza)
}
</script>

<style scoped>
.pizza-image {
  width: 100%;
  height: 500px;
  object-fit: cover;
  margin: 0 auto;
}
h1 {
  text-align: center;
  font-size: 60px;
}

.card {
  background-color: #d7773c;
  border-radius: 5px;
  width: 22%;
  padding: 10px;
  margin-bottom: 20px;
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
}

.pizza-btn:hover {
  background-color: #4f3a29;
  transform: translateY(-2px);
}
</style>
