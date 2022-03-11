<script setup>
import { ref } from 'vue'

let id = 0

const newTodo = ref('')
const todos = ref([

])

function addTodo() {
  todos.value.push({ id: id++, text: newTodo.value })
  newTodo.value = ''
}

function removeTodo(todo) {
  todos.value = todos.value.filter((t) => t !== todo)
}



</script>

<template>
  <input v-model="newTodo" @keyup.enter="addTodo">
  <button @click="addTodo">Add Todo</button>
  <ul>
    <li  @click="e => e.target.classList.toggle('done')" class="" v-for="todo in todos" :key="todo.id">
      {{ todo.text }}
      
      
      
      <button @click="removeTodo(todo)">X</button>
      
    </li>
  </ul>

  
</template>
 
 <style>


.done {
  text-decoration: line-through;
  
}

 </style>
