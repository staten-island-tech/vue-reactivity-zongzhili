<template>
  <div class="card">
    <img :src="pizza.image" alt="" class="pizza-image" />
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
  height: 350px;
  object-fit: cover;
  margin: 0 auto;
}
h1 {
  text-align: center;
  font-size: 60px;
}

.card {
  border-radius: 5px;
  background-color: white;
  width: 28%;
  padding: 18px;
  margin-bottom: 20px;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
  transition:
    transform 0.5s ease,
    box-shadow 0.5s ease;
}

.card:hover {
  transform: scale(1.05);
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
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
  transition: background-color 0.3s ease;
}

.pizza-btn:hover {
  background-color: #4f3a29;
}
</style>
