<template>
  <div class="task">
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

<style>
.task:hover {
  cursor: move;
}
</style>
