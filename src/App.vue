<script setup>
import { reactive, ref } from "vue";

const inputTodo = ref("");
const todo = reactive([]);

const addTodo = () => {
  if (inputTodo.value.trim() === '') return;
  const newTodo = {
    'id': crypto.randomUUID(),
    'work': inputTodo.value,
  }
  inputTodo.value = '';
  todo.push(newTodo);
}

</script>

<template>
  <div class="container">
    <div class="banner">
      <h2 class="banner__title">Todo list</h2>
    </div>

    <div class="main">
      <div class="input-group">
        <input
          type="text"
          class="input-add-todo"
          placeholder="Add todo..."
          v-model="inputTodo"
          @keyup.enter="addTodo"
        />
        <button class="btn-add-todo" @click="addTodo">+</button>
      </div>
      <div class="card" v-for="item in todo" :key="item.id">
        <input type="checkbox" class="input-checkbox-item" />
        <p>{{ item.work }}</p>
      </div>
    </div>
  </div>
</template>

<style scoped>
.container {
  width: 420px;
  background-color: slategray;
  height: 600px;
  padding: 16px;
  border-radius: 16px;
  box-shadow: rgba(50, 50, 93, 0.25) 0px 50px 100px -20px,
    rgba(0, 0, 0, 0.3) 0px 30px 60px -30px;
  position: relative;
}

.banner {
  background-color: aliceblue;
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 80px;
  border-top-left-radius: 16px;
  border-top-right-radius: 16px;
  display: flex;
  justify-content: center;
  align-items: center;
}

.main {
  margin-top: 100px;
}

.input-group {
  position: relative;
  margin-bottom: 30px;
}

.btn-add-todo {
  position: absolute;
  top: 0;
  right: 0;
  width: 34px;
  height: 34px;
  border: none;
  border-radius: 24px;
  transform: translate(-15px, 15%);
  background-color: slategrey;
}

.btn-add-todo:hover {
  cursor: pointer;
}

.btn-add-todo:active {
  opacity: 0.8;
}

.input-add-todo {
  border-radius: 20px;
  border: none;
  outline: none;
  background-color: aliceblue;
  padding: 14px 16px;
  width: 100%;
}

.card {
  background-color: aliceblue;
  border-radius: 4px;
  padding: 8px 16px;
  display: flex;
  margin-bottom: 12px;
}

.input-checkbox-item {
  margin-right: 30px;
}
</style>
