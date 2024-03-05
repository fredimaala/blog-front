<script setup>
import { ref, computed } from 'vue';

let i = 0;
let messege = ref('Hello Vue');

let items = ref([
  {id: i++, name:'sai', isDone: false},
  {id: i++, name:'munad', isDone: false},
  {id: i++, name:'piim', isDone: true},
  {id: i++, name:'viin', isDone: false},
  {id: i++, name:'suits', isDone: true},
]);
function add() {
  if (messege.value.trim() !== '') {
    items.value.push({id: i++, name:messege.value.trim(), isDone: true},);
  }
  messege.value = '';
}
let doneItems = computed(() => {
  return items.value.filter(item => item.isDone);
});
let toDoItems = computed(() => {
  return items.value.filter(item => !item.isDone);
});
</script>
<template>
<button @click="add">Click Me</button>
<input type="text" v-model="messege" @keydown.enter="add">

<h1>All items</h1>
<ul>
  <li v-for="item in items" :key="item.id">
    {{ item.name }}
    <input type="checkbox" v-model="item.isDone">
  </li>
</ul>

<h1>Done items</h1>
<ul>
  <li v-for="item in doneItems" :key="item.id">
    {{ item.name }}
    <input type="checkbox" v-model="item.isDone">
  </li>
</ul>

<h1>Todo items</h1>
<ul>
  <li v-for="item in toDoItems" :key="item.id">
    {{ item.name }}
    <input type="checkbox" v-model="item.isDone">
  </li>
</ul>
</template>


