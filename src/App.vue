<template>
  <div id="app">
    <task-list :tasks="tasks"></task-list>
  </div>
</template>

<script>
import TaskList from './components/TaskList.vue'

export default {
  name: 'app',
  components: {
    'task-list': TaskList,
  },
  data: function() {
    return  {
      tasks: [
        {
          title: 'Buy bananas',
          completed: true,
        },
        {
          title: 'Conquer the world',
          completed: false,
        }
      ]
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
