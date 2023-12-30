<template>
    <div class="container">
        
        <div class="display-box w-90 max-w-450 absolute top-1/2 left-1/2 transform -translate-x-1/2 -translate-y-1/2 bg-white p-50 md:p-60 lg:p-70 text-center">
            <h1 class="justify-center ">To Do List</h1>
            <form @submit.prevent="addTodo">
                <input v-model="newTodo">
                <button class="btn ml-4"> Add to List </button>
            </form>
            <ul>
                <li v-for="todo in todos" :key="todo.id">
                <input type="checkbox" v-model="todo.done" class="mr-2">
                <span :class="{done: todo.done}"> {{ todo.text }}</span>
                <button @click="removeTodo(todo)" class="btn ml-4 mb-1">X</button>
                </li>
            </ul>
        </div>
    </div>
</template>

<script setup>
    import { ref, computed} from 'vue'

    let id = 0
    //
    const newTodo = ref('')
    const todos = ref([])

    function addTodo(){
        todos.value.push({id: id++, text: newTodo.value, done: false})
        newTodo.value = ''
    }

    function removeTodo(todo) {
        todos.value = todos.value.filter((x) => x !== todo)
    }

</script>

<style scoped>
    .done{
        text-decoration: line-through;
    }

    html{
        background-color: black;
    }
</style>