<template>
  <div id="app">
    <Header />
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo" />
  </div>
</template>

<script>
import Header from './components/layouts/Header';
import Todos from './components/Todos';

export default {
  name: 'app',
  components: {
    Header,
    Todos
  },
  data(){
    return {
      todos: 
      [
        {
          id: 1,
          title: 'Todo Item 1',
          completed: true,
        },
        {
          id: 2,
          title: 'Todo Item 2',
          completed: true,
        },
        {
          id: 3,
          title: 'Todo Item 3',
          completed: false,
        },
      ]
    }
  },
  methods: {
    deleteTodo(id) {
      this.todos = this.todos.filter(todo => todo.id !== id);
    }
  }
}
</script>

<style>

</style>
