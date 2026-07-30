<script setup>
const props = defineProps({
  msg: String
})
</script>

<template>
  <h2>A Child Component!</h2>
  <p>{{ props.msg }}</p>
</template>