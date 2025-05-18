<template>
  <div>
    <div style="display: flex;">
      <label for="">Full name:</label>
      <p>{{ fullName }}</p>
    </div>


    <div style="display: flex;">
      <label for="">First name:</label>
      <p>{{ firstName }}</p>
    </div>

    <div style="display: flex;">
      <label for="">Last name:</label>
      <p>{{ lastName }}</p>
    </div>

    <button @click="changeName()">Change Name</button>
  </div>
</template>

<script setup>
import { ref, computed } from "vue";

const firstName = ref("Le Hoang");
const lastName = ref("Nhi");

const fullName = computed({
  get() {
    return firstName.value + ' ' + lastName.value;
  },
  set(newName) {
    [firstName.value, lastName.value] = newName.split(",");
  }
});

const changeName = () => fullName.value = "Doan Dang,Khoa";

</script>
