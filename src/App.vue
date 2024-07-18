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
  <h1>Submit the form Now!</h1>
  <!-- <button @click="displayForm? displayForm=false: displayForm=true">Show Form Link!</button> -->

  <button @click="toggleForm()">Show Form</button>

  <p>
    {{ displayForm? 'Form is Shared': 'Form is not visible' }}
  </p>

  <div v-show="displayForm">
    <form @submit.prevent="CreateTodo()">
    <label for="Description">Description: </label>
    <input v-model="data.todoDescription" id="Description" type="text" name="answer" required />
    <button >Submit</button>
  </form>
  </div>

  <ol>
    <li v-for="(todo,index) in data.todo">
      <del v-if="todo.isCompleted">{{ todo.description }} </del>
      <span v-else>{{ todo.description }} </span>
      <button @click="DeleteList(index)">Delete it</button>
      <button v-if="!todo.isCompleted" @click="Completed(index)">Completed Task</button>
    </li>
  </ol>
</template>

<script setup>

import { reactive } from 'vue';
import { ref } from 'vue';

const displayForm = ref(false);

const data = reactive({
  todo:[],
  todoDescription: "",
})

function CreateTodo() {
  console.log(data.todoDescription);
  data.todo.push({description: data.todoDescription,
    isCompleted: false,
  });
}

function DeleteList(index) {
  data.todo.splice(index,1);
}

function Completed(index) {
  data.todo[index].isCompleted=true;
}

function toggleForm() {
  displayForm.value = !displayForm.value;
}
</script>
