<script setup>
import { ref } from 'vue';


let messege = ref('Hello Vue');

let items = ref(['sai', 'munad', 'piim', 'viin', 'suits']);
function add() {
  if (messege.value.trim() !== '') {
    items.value.push(messege.value.trim());
  }
  messege.value = '';
}
</script>

<template>
  <button @click="add">Click Me</button>
  <input type="text" v-model="messege" @keydown.enter="add">
  <li v-for="item in items">{{ item }}</li>
</template>


