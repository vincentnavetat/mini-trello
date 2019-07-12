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
.task {
  background: #f5f5f5;
  display: flex;
  justify-content: space-between;
  padding: .5rem;
}

.task + .task {
  margin-top: 1rem;
}

.task:hover {
  cursor: move;
}
</style>
