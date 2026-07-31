<script setup>
const props = defineProps({
  msg: String
})

// //////////////////////////////////////////////
const emit = defineEmits(['response'])

emit('response', 'hello from child')
// //////////////////////////////////////////////
</script>

<template>
  <h2>A Child Component!</h2>
  <p>{{ props.msg }}</p>
  <slot>fallback</slot>
</template>