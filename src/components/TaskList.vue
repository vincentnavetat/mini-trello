<template>
  <main>
    <h1>To-do list</h1>
    <ul>
      <task v-for="(task, index) in tasks" v-bind:data="task" v-bind:key="index" :task="task" @remove="removeTask(index)">
      </task>
    </ul>

    <button @click="clearAllTasks">I'm all done with my tasks</button>

    <form v-on:submit.prevent="addTask">
      <input type="text" placeholder="Add new task" v-model="newTask">
      <input type="submit" value="Add">
    </form>
  </main>
</template>

<script>
import Task from './Task.vue'

export default {
  name: 'task-list',
  props: {
    tasks: {default: []}
  },
  data() {
    return {
      newTask: '',
    };
  },
  components: {
    'task' : Task,
  },
  methods: {
    addTask() {
      this.tasks.push({
        title: this.newTask,
        completed: false,
      });
      this.newTask = '';
    },
    removeTask(index) {
      this.tasks.splice(index, 1);
    },
    clearAllTasks() {
      this.tasks.map(task => task.completed = true);
    }
  }
}
</script>
