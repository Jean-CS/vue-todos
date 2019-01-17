<template>
  <div id="app">
    <img alt="Vue logo" src="../assets/logo.png">
    <AddTodo v-on:add-todo="addTodo"/>
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo"/>
  </div>
</template>

<script>
import axios from 'axios';

import Todos from '../components/Todos';
import AddTodo from '../components/AddTodo';

const apiUrl = 'https://jsonplaceholder.typicode.com/todos';

export default {
  name: "home",
  components: {
    Todos,
    AddTodo,
  },
  data() {
    return {
      todos: []
    }
  },
  methods: {
    deleteTodo(id) {
      axios.delete(`${apiUrl}/${id}`)
           .then(res => this.todos = this.todos.filter(todo => todo.id !== id))
           .catch(err => console.log(err));
    },
    addTodo({ id, title, completed }) {
      axios.post(apiUrl, { title, completed })
           .then(res => this.todos = [...this.todos, { id, title, completed }] )
           .catch(err => console.log(err));
    }
  },
  // Similar to componentDidMount() in React
  created() {
    axios.get(apiUrl, {
      params: {
        _limit: 5
      }
    })
    .then(res => this.todos = res.data)
    .catch(err => console.log(err))
  }
};
</script>

<!-- This is a global style -->
<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
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
