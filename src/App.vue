<!-- 
<template>
  <h1>Hello World</h1>
  <button v-on:click="increment()">Increment</button>
  <button v-on:click="reset()">Reset</button>
  <p>{{ data.count }}</p>
</template>

<script setup>

import { reactive } from "vue"

const data = reactive({
  count:0
});

function increment() {
  data.count+=1;
}

function reset() {
  data.count=0;
}
</script> -->

<template>
  <form @submit.prevent="CreateTodo()">
    <label for="description">Description: </label>
    <input v-model="data.todoDescription" id="description" type="text" name="answer">
    <input type="submit" value="Add-On"/>
  </form>

  <!-- <pre>{{ data.todoDescription }}</pre> -->
  <ol>
    <li v-for="todo in data.todos">{{ todo }}</li>
  </ol>
</template>

<script setup>

import { reactive } from 'vue';

const data = reactive({
  todos:[],
  todoDescription:"",
})

function CreateTodo() {
  console.log("Hello World");
  // data.todos.push("Buy me Milk!");
  data.todos.push(data.todoDescription);
  data.todoDescription="";
}
</script>