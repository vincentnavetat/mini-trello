<template>
  <div id="app">
    <column :tasks="tasks"></column>
  </div>
</template>

<script>
import Column from './components/Column.vue'

export default {
  name: 'app',
  components: {
    'column': Column,
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
