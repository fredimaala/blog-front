<script setup>
import { ref, computed } from 'vue';
import ItemList from './components/ItemList.vue';

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

<ItemList :items="items" title="All items"></ItemList>
<ItemList :items="doneItems" title="Done items"></ItemList>
<ItemList :items="toDoItems" title="Todo items"></ItemList>

</template>


