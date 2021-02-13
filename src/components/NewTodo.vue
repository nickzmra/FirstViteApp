<template>
    <input 
    class="text-2xl py-2 px-4 rounded-xl mt-6" 
    type="text" 
    placeholder="New Task" 
    v-model="newTodo" 
    @change="addTodo"
    />
</template>

<script setup>
import {newTodo, addTodo} from '../helpers/useTodos'
</script>