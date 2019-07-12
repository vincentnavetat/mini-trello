<template>
  <div>
    {{ task.title }}
    <button @click="$emit('remove')">x</button>
  </div>
</template>

<script>
export default {
  name: 'task',
  props: ['task'],
}
</script>

