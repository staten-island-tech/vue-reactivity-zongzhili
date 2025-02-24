<template>
  <div class="cart">
    <h1>Cart</h1>
    <h2>Total: ${{ total }}<br />Items:</h2>
    <div v-for="(pizza, index) in cart" :key="index" class="cart-item">
      <img :src="pizza.image" alt="" class="cart-image" />
      <p>{{ pizza.name }} Pizza- ${{ pizza.price }}</p>
      <button class="removebtn" @click="removeCart(index)">Remove</button>
    </div>
  </div>
</template>

<script setup>
defineProps({
  cart: Array,
  total: Number,
})
const emit = defineEmits(['removeCart'])
function removeCart(index) {
  emit('removeCart', index)
}
</script>

<style scoped>
.cart-item {
  display: flex;
  align-items: center;
  flex-direction: row;
  gap: 10px;
  padding: 10px;
  border-radius: 5px;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
  margin-bottom: 10px;
  border: 1px solid black;
}
.cart-image {
  width: 50px;
  height: 50px;
  object-fit: cover;
  border-radius: 5px;
}
.removebtn {
  background-color: #b52121;
  color: white;
  border: none;
  padding: 10px 20px;
  font-size: 16px;
  border-radius: 5px;
  transition: 0.5s ease;
}
.removebtn:hover {
  transform: scale(1.1);
}
@media (max-width: 1600px) {
  .cart-item {
    flex-direction: column;
  }
}
</style>
