<template>
  <div id="app">
    <!-- Use v-on to receive id value from del-todo and then call method to delete that todo item -->
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo"/>
  </div>
</template>

<script>
import Todos from './components/Todos.vue';

export default {
  name: 'app',
  components: {
    Todos
  },
  data () {
    return {
      todos: [
        {
          id: 1,
          title: "Become famous",
          completed: false
        },
          {
          id: 2,
          title: "Sell film rights to my life",
          completed: true
        },
          {
          id: 3,
          title: "Retire and live on luxury yaught",
          completed: false
        }
      ]
    }
  },
  methods: {
    deleteTodo(id) {
// Use filter method to select every id in the array apart from that which has been selected by the id clicked.
      this.todos = this.todos.filter(todo => todo.id !== id);
    }
  }
}
</script>

<style>
  * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }

  body {
    font-family: Arial, Helvetica, sans-serif;
    line-height: 1.4;
  }
</style>
