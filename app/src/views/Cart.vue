<template>
  <div class="cart">
    <h1>Cart</h1>
    <h2>Total: ${{ total }}<br />Items:</h2>
  </div>
</template>

<script setup>
defineProps({
  cart: Array,
  total: Number,
})
</script>

<style scoped></style>
