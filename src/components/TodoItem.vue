<template>
    <div class="todo-item" v-bind:class="{'is-completed':todo.completed}">
        <input type="checkbox" v-on:change="markComplete">
        <p>{{ todo.title }}</p>
        <button @click="$emit('del-todo', todo.id)" class="del" >x</button>
    </div>
</template>

<script>
export default {
    name: "TodoItem",
    props: ["todo"],
    methods: {
        markComplete() {
            this.todo.completed = !this.todo.completed;
        }
    }
}
</script>

<style scoped>
    .todo-item {
        background: #f4f4f4;
        padding: 10px;
        border-bottom: 1px #ccc dotted;
    }

    .is-completed {
        text-decoration: line-through;
    }

    .del {
        background: red;
        border: 1px black solid;
        border-radius: 25px;
    }
</style>