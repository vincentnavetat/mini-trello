<template>
  <div id="app">
    <h1>To-do list</h1>

    <column v-for="(column, index) in columns" v-bind:column="column" v-bind:key="index" :columns="columns">
    </column>
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
      columns: [
        {
          title: 'first',
          tasks: [
            {
              title: 'Buy bananas',
              completed: true,
            },
            {
              title: 'Conquer the world',
              completed: false,
            }
          ],
        },
        {
          title: 'second',
          tasks: [
            {
              title: 'Buy bananas',
              completed: true,
            },
            {
              title: 'Conquer the world',
              completed: false,
            }
          ],
        },
      ],
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
</style>
