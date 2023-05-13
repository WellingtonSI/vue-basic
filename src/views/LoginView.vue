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

 function remove(user){
    const index = names.findIndex( name  => {
       return name.firstName == user.firstName
    })

    names.splice(index, 1)
 }
</script>

<template>

    <h1 class="font-bold text-3xl text-blue-900">Login</h1>

    <template v-if="names.length > 0">
        <ul>
            <li v-for ="name in names">{{ name.firstName }} - <button v-on:click="remove(name)">Remove</button> </li>
        </ul>
    </template>
    <template v-else>Nenhum user encontrado</template>


    <template v-if="user.email.length <= 0"><br>Email Vazio</template>
    <template v-else>Email: {{ user.email }}</template>
    


    <form action="" @submit.prevent="login">
        <input type="text" placeholder="E-mail" v-model="user.email">
        <input type="text" placeholder="Password" v-model="user.password">
        <button type="submit">Login</button>
    </form>
</template>

<style>
</style>