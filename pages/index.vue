<template>
    <h1>To Do List</h1>
    <form @submit.prevent="addTodo">
        <input v-model="newTodo">
        <button> Add to List </button>
    </form>
    <ul>
        <li v-for="todo in todos" :key="todo.id">
        <input type="checkbox" v-model="todo.done">
        <span :class="{done: todo.done}"> {{ todo.text }}</span>
        <button @click="removeTodo(todo)">X</button>
        </li>
    </ul>
    <button @click="hideTodo != hideTodo">
        {{ hideTodo ? 'Show all' : 'Hide Completed' }}
    </button>
</template>

<script setup>
    import { ref } from 'vue'

    let id = 0
    //
    const newTodo = ref('')
    const hideTodo = ref(false)
    const todos = ref([
        {id: id++, text: "jas", done: false}
    ])

    function addTodo(){
        todos.value.push({id: id++, text: newTodo.value, done: false})
        newTodo.value = ''
    }

    function removeTodo(todo) {
        todos.value = todos.value.filter((x) => x !== todo)
    }

</script>

<style lang="css" scoped>
    .done{
        text-decoration: line-through;
    }
</style>