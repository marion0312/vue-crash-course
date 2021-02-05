<template>
  <div id="app">
    <Header />
    <AddTodo v-on:add-todo="addTodo" />
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo" />
  </div>
</template>

<script>
import Header from './components/layouts/Header';
import Todos from './components/Todos';
import AddTodo from './components/AddTodo';
import axios from 'axios';

export default {
  name: 'app',
  components: {
    Header,
    Todos,
    AddTodo
  },
  data(){
    return {
      todos: 
      [
        // {
        //   id: 1,
        //   title: 'Todo Item 1',
        //   completed: true,
        // },
        // {
        //   id: 2,
        //   title: 'Todo Item 2',
        //   completed: true,
        // },
        // {
        //   id: 3,
        //   title: 'Todo Item 3',
        //   completed: false,
        // },
      ]
    }
  },
  methods: {
    deleteTodo(id) {
      axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
      .then(res => this.todos = this.todos.filter(todo => todo.id !== id, res.data))
      .catch(err => console.log(err));
    },
    addTodo(newTodo) {
      const { title, completed } = newTodo;

      axios.post('https://jsonplaceholder.typicode.com/todos', {
        title, 
        completed,
      })
      .then(res => this.todos = [...this.todos, res.data])
      .catch(err => console.log(err));

      this.todos = [...this.todos, newTodo];
    }
  },
  // NOT INSIDE METHODS!
  created() {
    axios.get('https://jsonplaceholder.typicode.com/todos?_limit=5')
    .then(res => this.todos = res.data)
    .catch(err => console.log(err));
  }
}
</script>

<style>
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
