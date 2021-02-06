<template>
  <div id="app">
    <AddTodo v-on:add="AddTodo"/>
   <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo" />
  </div> 
</template>

<script>
import Todos from '../components/Todos'; 
import AddTodo from '../components/AddTodo';
import axios from 'axios';
export default {
  name: 'Home',
  components: {
    Todos,
    AddTodo
  },
  data() {
    return {
      todos: []
    }
  },
  methods: {
    deleteTodo(id) {
        axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
        // eslint-disable-next-line
        .then (res => this.todos = this.todos.filter(todo => todo.id != id))
        .catch(err => console.log(err));
      },
    addTodo(newTodo) {
      const { title, completed } = newTodo;
      
      axios.post('https://jsonplaceholder.typicode.com/todos', {title,completed})
      .then(res => this.todos = [...this.todos, res.data] )
      .catch(err => console.log(err));
      }
    },
  created() {
    axios.get('https://jsonplaceholder.typicode.com/todos?_limit=5')
      .then(res => this.todos = res.data)
      .catch(err => console.log(err));

  }
}

</script>

<style scoped>
  * {
    box-sizing: border-box;
    margin: 1cm;
    padding: 2cm;
    }

  body {
    font-family: Courier New, Courier, monospace;
    line-height: 1.4;
  }

  btn {
    display: inline-block;
    border:none;
    background: black;
    color:white;
    padding: 2px 2px;
    cursor: pointer;
  }

  .btn:hover {
    background: yellow;
  }
</style>

