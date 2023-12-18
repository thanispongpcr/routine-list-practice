<script setup>
import { ref } from "vue";

let id = 0;
const items = ref([
  { id: id++, routine: "ตื่น" },
  { id: id++, routine: "กิน" },
  { id: id++, routine: "นอน" },
]);

const newRoutine = ref("");

const addRoutine = () => {
  let itemObj = {
    id: id++,
    routine: newRoutine.value,
  };
  items.value.push(itemObj);
};

const deleteRoutine = (item) => {
  items.value = items.value.filter((it) => it !== item);
};
</script>

<template>
  <div>
    <h1>My Routine</h1>
    <input v-model="newRoutine" />
    <button @click="addRoutine()">+</button>
    <ul>
      <li v-for="item in items" :key="item.id">
        <h2>{{ item.routine }}</h2>
        <button @click="deleteRoutine(item)">x</button>
      </li>
    </ul>
  </div>
</template>

<style scoped>
ul li {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 200px;
}
</style>
