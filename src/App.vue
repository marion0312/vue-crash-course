<template>
  <div id="app">
    <Todos />
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
          completed: false,
        },
        {
          id: 2,
          title: 'Todo Item 2',
          completed: false,
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
