<template>
  <div id="app">
    <!-- Use v-on to listen for data and update the dom -->
    <AddTodo v-on:add-todo="addTodo" />
    <!-- Use v-on to receive id value from del-todo and then call method to delete that todo item -->
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo" />
  </div>
</template>

<script>
import Todos from "../components/Todos";
import AddTodo from "../components/AddTodo";
import axios from "axios";

// Don't forget! Each component must be 1) Imported, 2) Listed in export default (below) and 3. included in the html at the top of this file
export default {
  name: "Home",
  components: {
    AddTodo,
    Todos
  },
  data() {
    return {
      todos: []
    };
  },
  methods: {
    deleteTodo(id) {
      // use axios rather than fetch (preference in tutorial) to delete todo from database
      // Use filter method to select every id in the array apart from that which has been selected by the id clicked and delete from UI
      axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
      .then(res => this.todos = this.todos.filter(todo => todo.id !== id))
      .catch(err => console.log (err));

    },
    addTodo(newTodo) {
      //Destructuring - pull out title and completed from new Todo object
      const {title, completed} = newTodo;

      // Post a todo to jsonplaceholder site which simulates storing it in a database
      axios.post('https://jsonplaceholder.typicode.com/todos', {
        title,
        completed
      })
      .then(res => this.todos = [...this.todos, newTodo])
      .catch(err => console.log (err));
      // Use spread operator to copy what it in todos and add to it.
      // this.todos = [...this.todos, newTodo];
      // this.title = "";
    },
    
    
  },
  // Use created method to run this when the component loads
  created() {
    axios.get('https://jsonplaceholder.typicode.com/todos?_limit=5')
    .then(res => this.todos = res.data)
    .catch(err => consols.log(err));
  }
};
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

.btn {
  display: inline-block;
  border: none;
  background: #555;
  color: #fff;
  padding: 7px 20px;
  cursor: pointer;
}

.btn:hover {
  background: #666;
}
</style>
