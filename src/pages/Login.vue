<script setup>
import { ref } from 'vue';
import axios from 'axios';
axios.defaults.withCredentials = true;
axios.defaults.withXSRFToken = true;
try {
    let response = await axios.get('http://localhost:8000/api/user');
} catch(err){
}
let email = ref('');
let password = ref('');
async function login(){
    let response = await axios.get('http://localhost:8000/sanctum/csrf-cookie');
    response = await axios.post('http://localhost:8000/api/login', {
            email: email.value,
            password: password.value
    });
}
</script>
<template>
    <div class="container">
    <b-field label="Email">
            <b-input type="email" v-model="email"></b-input>
    </b-field>
    <b-field label="Password">
        <b-input type="password" v-model="password"></b-input>
    </b-field>
    <b-button @click="login">Login</b-button>
    </div>
</template>