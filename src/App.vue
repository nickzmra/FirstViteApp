<template>
  <div class="min-h-screen flex flex-col justify-center items-center">
    <header class="flex flex-col w-full container">
      <h1 class="text-6xl text-gray-700 font-light text-center">My To-Do App</h1>
      <input class="text-2xl py-2 px-4 rounded-xl mt-6" type="text" placeholder="New Task" v-model="newTodo" @change="addTodo"/>
    </header>

    <main class="container w-full mt-4 space-y-4">
      <section class="space-y-2" v-if="pendingTodos.length > 0">
        <h3 class="text-3xl font-thin text-green-500">Pending Items: {{ pendingTodos.length }}</h3>
        <ul class="space-y-2">
          <li 
          v-for="todo in pendingTodos" 
          :key="todo.id" 
          class="bg-white rounded-xl text-2xl py-2 px-4 font-thin text-center hover:text-white hover:bg-green-600 transition-colors" 
          @click="changeStatus(todo.id)"
          >
            {{ todo.text }}
          </li>
        </ul>
      </section>

      <section class="space-y-2" v-if="completedTodos.length > 0">
        <h3 class="text-3xl font-thin text-red-500 mt-4">Completed Items: {{ completedTodos.length }}</h3>
        <ul class="space-y-2">
          <li 
          v-for="todo in completedTodos" 
          :key="todo.id" 
          class="bg-white rounded-xl text-2xl py-2 px-4 font-thin text-center hover:text-white hover:bg-red-600 transition-colors"
          @click="changeStatus(todo.id)"
          >
            {{todo.text}}
          </li>
        </ul>
      </section>
    </main>
  </div>
</template>

<script setup>
import {ref, computed} from 'vue'

const newTodo = ref('')

const todos = ref([])

const pendingTodos = computed(() =>
  todos.value.filter(todo => todo.status === 'pending'),
)

const completedTodos = computed(() =>
  todos.value.filter(todo => todo.status === 'done'),
)

const changeStatus = id => {
  todos.value.map(todo => {
    if (todo.id === id) {
      todo.status = todo.status === 'pending' ? 'done' : 
      'pending'
    }
  })
}

const addTodo = () => {
  if (newTodo.value.length > 0) {
    todos.value.push( {
      id: todos.value.length,
      text: newTodo.value,
      status: 'pending',
    })
    newTodo.value = ''
  }
}
</script>