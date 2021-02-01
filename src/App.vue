<template>
  <div id="app">
    <Todos v-bind:todos="todos" />
  </div>
</template>

<script>
import Todos from './components/Todos';

export default {
  name: 'app',
  components: {
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
  }
}
</script>

<style>

</style>
