<template>
  <div class="column">
    <header class="column__header">
      <div class="title__text" @click="editTitle" ref="title">{{ column.title }}</div>
      <input type="test" v-model="column.title" class="title__input hide" ref="titleInput" @blur="quitEditTitle">
      <button @click="$emit('remove')">x</button>
    </header>

    <draggable
        :list="column.tasks"
        class="tasks"
        ghost-class="ghost"
        @start="dragging = true"
        @end="dragging = false"
      >
      <task v-for="(task, index) in column.tasks" v-bind:task="task" v-bind:key="index" :tasks="column.tasks" @remove="removeTask(index)">
      </task>
    </draggable>

    <form class="create-task" v-on:submit.prevent="addTask">
      <input type="text" placeholder="Add new task" v-model="newTask" class="create-task__title">
      <input type="submit" value="Add">
    </form>
  </div>
</template>

<script>
import draggable from "vuedraggable";
import Task from './Task.vue'

export default {
  name: 'column',
  props: ['column'],
  data() {
    return {
      newTask: '',
    };
  },
  components: {
    draggable,
    'task' : Task,
  },
  methods: {
    editTitle() {
      this.$refs.title.classList.add('hide');
      this.$refs.titleInput.classList.add('show');
      this.$refs.titleInput.focus();
    },
    quitEditTitle() {
      this.$refs.title.classList.remove('hide');
      this.$refs.titleInput.classList.remove('show');
    },
    addTask() {
      this.column.tasks.push({
        title: this.newTask,
        completed: false,
      });
      this.newTask = '';
    },
    removeTask(index) {
      this.column.tasks.splice(index, 1);
    },
  }
}
</script>

<style>
.column {
  background: white;
  border: 1px solid black;
  border-radius: 2px;
  padding: 1rem;
}

.column__header {
  display: flex;
  justify-content: space-between;
}

.title__text,
.title__input {
  font-size: 1.5rem;
  font-weight: bold;
}

.tasks {
  margin: 1rem 0;
}

.create-task {
  display: flex;
}

.create-task__title {
  display: flex;
  flex: 1;
}
</style>
