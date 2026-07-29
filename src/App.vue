<!-- https://vuejs.org/tutorial/#step-8-->
<script setup>
import { ref, reactive, computed } from 'vue'


//ref makes a single reactive value (primitive or object) and can be reassigned
const titleClass = ref('title')
const message = ref('Hello World!')
const text = ref('')

console.log(message.value) // "Hello World!"
message.value = 'Changed'


// ///////////////////////////////////////
//reactive makes an object reactive but cannot be reassigned
const counter = reactive({
  count: 0
})

console.log(counter.count) // 0
counter.count++

function increment() {
  counter.count++;
}
// ///////////////////////////////////////

// ///////////////////////////////////////
const awesome = ref(false)
function toggle() {
  awesome.value = !awesome.value;
}
// ///////////////////////////////////////

// ///////////////////////////////////////
// give each todo a unique id
let id = 0

const hideCompleted = ref(false)
const filteredTodos = computed(() => {
  // return filtered todos based on
  // `todos.value` & `hideCompleted.value`
    return hideCompleted.value
    ? todos.value.filter((t) => !t.done)
    : todos.value
})
const newTodo = ref('')
const todos = ref([
  { id: id++, text: 'Learn HTML' , done:false},
  { id: id++, text: 'Learn JavaScript' , done:false},
  { id: id++, text: 'Learn Vue' , done:false}
])


function addTodo() {
  // ...
  //newTodo.value = ''
  todos.value.push({ id: id++, text: newTodo.value , done:false});
}

function removeTodo(todo) {
  // ...
  todos.value = todos.value.filter(t=>t.id!==todo.id);
}
// ///////////////////////////////////////

</script>

<template>
  <h1 :class="titleClass">{{ message }}</h1>
  <div>
  <p>Count is: {{ counter.count }}</p>
  <button @click="increment">Count is: {{ count }}</button>
</div>

<div>
    <input v-model="text" placeholder="Type here">
  <p>Text should appear here: {{ text }}. and end at the dot</p>
  </div>

  <div>
     <button @click="toggle">Toggle</button>
  <h1 v-if="awesome">Vue is awesome!</h1>
  <h1 v-else>Oh no 😢</h1>
  </div>

  <div>
    <form @submit.prevent="addTodo">
      <input v-model="newTodo" required placeholder="new todo">
      <button>Add Todo</button>
    </form>
    <ul>
      <li v-for="todo in filteredTodos" :key="todo.id">
           <input type="checkbox" v-model="todo.done">
        <span :class="{ done: todo.done }">{{ todo.text }}</span>
        <button @click="removeTodo(todo)">X</button>
      </li>
    </ul>
  <button @click="hideCompleted = !hideCompleted">
    {{ hideCompleted ? 'Show all' : 'Hide completed' }}
  </button>
  </div>
</template>

<style scope>
.title {
  color: red;
}
.done {
  text-decoration: line-through;
}
</style>
