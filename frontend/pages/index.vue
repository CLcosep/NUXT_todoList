<template>
    <h1 class="">To Do List</h1>
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
    <button @click="hideTodo = !hideTodo">
        {{ hideTodo ? 'Show all' : 'Hide Completed' }}
    </button>
</template>

<script setup>
    import { ref, computed} from 'vue'

    let id = 0
    //
    const newTodo = ref('')
    const hideTodo = ref(false)
    const todos = ref([])

    const filteredTodos = computed(() => {
  return hideTodo.value
    ? todos.value.filter((t) => !t.done)
    : todos.value
})

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
    .btn {
        @apply bg-[#beabed] text-white px-3 py-2  rounded-md text-sm text-white;
    }
</style>