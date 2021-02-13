<template>
  <div class="min-h-screen flex flex-col justify-center items-center">
    <Header/>
    <Main>
      <ListTodos color="green" title="Pending Items" :todos="pendingTodos"/>
      <ListTodos color="red" title="Completed Items" :todos="completedTodos"/>
    </Main>
  </div>
</template>

<script setup>
import Main from './components/Main.vue'
import ListTodos from './components/ListTodos.vue'
import Header from './components/Header.vue'
import {pendingTodos, completedTodos} from './helpers/useTodos'
</script>