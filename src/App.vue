<template>
  <main id="app">
    <header>
      <h1>Mini Trello</h1>
    </header>

    <div class="columns">
      <column v-for="(column, index) in columns" v-bind:column="column" v-bind:key="index" :columns="columns">
      </column>
    </div>
  </main>
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
          title: 'To-do',
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
          title: 'In progress',
          tasks: [
            {
              title: 'Learning VueJS',
              completed: true,
            },
            {
              title: 'Do something',
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

.columns {
  display: grid;
  grid-template-columns: repeat(6, 1fr);
  column-gap: 1rem;
}
</style>
