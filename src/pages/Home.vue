<script setup>
import axios from 'axios';
import {ref} from 'vue';
let posts = ref([]);
axios.get('http://localhost:8000/api/posts').then(res =>{
    console.log(res);
    posts.value = res.data.data
})
</script>
<template>
    <h1>Home</h1>
    <ul>
        <li v-for="post in posts">{{ post.title }}</li>
    </ul>
</template>