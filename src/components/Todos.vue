<template>
<div>
    <div v-bind:key="todo.id" v-for="todo in todos">
        <!-- Use v-on and $emit to receive deleted vale from Todoitem click event an padd this up to App.vue to remove todo item -->
        <TodoItem v-bind:todo="todo" v-on:del-todo="$emit('del-todo',todo.id)"/>
    </div>
</div>
</template>

<script>
import TodoItem from './Todoitem.vue';

export default {
name: "Todos",
components: {
    TodoItem
},
props: ["todos"]
}
</script>

<style scoped>

</style>
