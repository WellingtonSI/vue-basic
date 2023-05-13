<script setup>

import {ref, reactive, onMounted} from 'vue';

const email = ref('')
const password = ref('')

const user = reactive({
    email:'',
    password:''
})

const names = reactive([])

onMounted( () => {
    names.push(
        {
            firstName:'Alexandre',
            age:40
        },
        {
            firstName:'Maria',
            age:25
        },
        {
            firstName:'João',
            age:31
        },
    );
})

 function login(){
    console.log(user);
 }

 function remove(name){
    const index = names.findIndex( name )
 }
</script>

<template>


    <template v-if="names.length > 0">
        <ul>
            <li v-for ="name in names">{{ name.firstName }} - <button v-on:click="remove(name)">Remove</button> </li>
        </ul>
    </template>
    <template v-if="user.email.length <= 0">Email Vazio</template>
    <template v-else>Email: {{ user.email }}</template>


    <form action="" @submit.prevent="login">
        <input type="text" placeholder="E-mail" v-model="user.email">
        <input type="text" placeholder="Password" v-model="user.password">
        <button type="submit">Login</button>
    </form>
</template>

<style>
</style>