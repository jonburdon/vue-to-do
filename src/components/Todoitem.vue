<template>
<!-- Add a class based on a condition - is-complete -->
    <div class="todo-item" v-bind:class="{'is-complete':todo.completed}">

<p>
    <!-- Add an event, use v-on directive using method called markComplete -->
    <input type="checkbox" v-on:change="markComplete">
{{todo.title}}
<!-- Use $emit to delete a todo, pass value to del-todo and pass this up to Todos -->
<button @click="$emit('del-todo', todo.id)" class="del">x</button>
</p>
    </div>
</template>

<script>
export default {
    name: "Todoitem",
    props: ["todo"],
    methods: {
        markComplete() {
            this.todo.completed = !this.todo.completed
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

.is-complete {
    text-decoration: line-through;
}

.del {
    background: #ff0000;
    color: #fff;
    border: none;
    padding: 5px 9px;
    border-radius: 50%;
    cursor: pointer;
    float: right;
}
</style>
