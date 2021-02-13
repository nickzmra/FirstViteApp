<template>
    <section class="space-y-2" v-if="todos.length > 0">
        <h3 class="text-3xl font-thin" 
        :class="
            color === 'green' ? 'text-green-600' : 'text-red-600'"
            >
                {{title}}: {{ todos.length }}</h3>
        <ul class="space-y-2">
          <li 
          v-for="todo in todos" 
          :key="todo.id" 
          class="bg-white rounded-xl text-2xl py-2 px-4 font-thin text-center hover:text-white transition-colors"
          :class="
            color === 'green' ? 'text-green-500 hover:bg-green-500' : 'text-red-500 hover:bg-red-500'" 
          @click="changeStatus(todo.id)"
          >
            {{ todo.text }}
          </li>
        </ul>
      </section>
</template>

<script setup>
import {defineProps} from 'vue'
import {changeStatus} from '../helpers/useTodos'

defineProps({
    color: {
        type: String,
        default: 'green',
    },
    title: {
        type: String,
        default: 'To Do List',
    },
    todos: {
        type: Array,
        default: [],
    },
})
</script>