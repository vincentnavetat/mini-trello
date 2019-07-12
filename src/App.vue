<template>
  <main id="app">
    <header>
      <h1>Mini Trello</h1>
    </header>

    <draggable
      v-model="columns"
      class="columns"
      @start="dragging = true"
      @end="dragging = false"
    >
      <column v-for="(column, index) in columns" v-bind:column="column" v-bind:key="index" :columns="columns" @remove="removeColumn(index)">
      </column>
    </draggable>

    <div>
      <button @click="addColumn()">Add new column</button>
    </div>
  </main>
</template>

<script>
import draggable from "vuedraggable";
import Column from './components/Column.vue'

export default {
  name: 'app',
  components: {
    draggable,
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
            },
            {
              title: 'Conquer the world',
            }
          ],
        },
        {
          title: 'In progress',
          tasks: [
            {
              title: 'Learning VueJS',
            },
            {
              title: 'Do something',
            }
          ],
        },
      ],
    }
  },
  methods: {
    addColumn() {
      this.columns.push({
        title: 'New col!',
        tasks: [],
      });
    },
    removeColumn(index) {
      this.columns.splice(index, 1);
    },
  }
}
</script>

<style>
body {
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

.hide {
  display: none;
}

.show {
  display: block;
}
</style>
