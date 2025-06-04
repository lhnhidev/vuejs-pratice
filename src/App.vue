<script setup>
import { ref, reactive, nextTick, computed } from "vue";

const store = [
  {
    name: "Trái táo",
    price: 12,
  },
  {
    name: "Bắp cải",
    price: 20,
  },
  {
    name: "Cà rốt",
    price: 2,
  },
];
</script>

<template>
  <div class="container">
    <ul>
      <li v-for="item in store" :key="item.name">
        {{ item.name }} - {{ item.price }}
      </li>
    </ul>
  </div>
</template>

<style scoped>
.container {
  background-color: #ccc;
  width: 100vw;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}

.button {
  padding: 8px;
  border-radius: 5px;
}

.active:active {
  background-color: blueviolet;
  color: white;
}

.has-error {
  background-color: red;
  color: white;
}
</style>
