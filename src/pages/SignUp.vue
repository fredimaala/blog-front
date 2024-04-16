<script setup>
import { ref } from 'vue';
import axios from 'axios';

axios.defaults.withCredentials = true;
axios.defaults.withXSRFToken = true;

let name = ref('');
let email = ref('');
let password = ref('');

async function register() {
    try {
        let response = await axios.post('http://localhost:8000/sanctum/csrf-cookie');
        response = await axios.post('http://localhost:8000/api/register', {
            name: name.value,
            email: email.value,
            password: password.value
        });
        console.log('User registered successfully:', response.data);
        // Optionally, you can redirect the user to another page or show a success message here
    } catch(err) {
        console.error('Error registering user:', err);
        // Handle errors, e.g., display an error message to the user
    }
}
</script>

<template>
    <div class="container">
        <b-field label="Name">
            <b-input type="text" v-model="name"></b-input>
        </b-field>
        <b-field label="Email">
            <b-input type="email" v-model="email"></b-input>
        </b-field>
        <b-field label="Password">
            <b-input type="password" v-model="password"></b-input>
        </b-field>
        <b-button @click="register">Register</b-button>
    </div>
</template>
