<template>
  <div class="cart">
    <h1>Cart</h1>
    <div v-if="cart.length === 0">Your cart is empty.</div>
    <h2>Total: $<br />Items:</h2>
  </div>
</template>

<script setup>
defineProps({
  cart: Array,
})
</script>

<style scoped></style>
