<!-- https://vuejs.org/tutorial/#step-4-->
<script setup>
import { ref } from 'vue'
import { reactive } from 'vue'


const titleClass = ref('title')
const message = ref('Hello World!')

console.log(message.value) // "Hello World!"
message.value = 'Changed'


const counter = reactive({
  count: 0
})

console.log(counter.count) // 0
counter.count++

</script>

<template>
  <h1>Make me dynamic!</h1>
  <h1 :class="titleClass">{{ message }}</h1>
  <p>Count is: {{ counter.count }}</p>
</template>

<style scope>
.title {
  color: red;
}
</style>
