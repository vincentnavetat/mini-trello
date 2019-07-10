<template>
  <li>
    <label class="task" v-bind:class="{ 'task--completed': task.completed }">
      {{ task.title }}
      <input type="checkbox" v-bind:checked="task.completed" @click="toggleComplete">
    </label>
    <button @click="$emit('remove')">Remove</button>
  </li>
</template>

<script>
export default {
  name: 'task',
  props: ['task'],
  methods: {
    toggleComplete: function () {
      this.task.completed = !this.task.completed;
    },
  }
}
</script>

<style>
.task {
  cursor: 'pointer';
}

.task--completed {
  text-decoration: line-through;
}
</style>
