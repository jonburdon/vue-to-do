<template>
    <div>
        <form @submit="addTodo">
            <!-- Use v-model directive with name so the title field data can be used -->
            <input type="text" v-model="title" name="title" placeholder="Add Goal ...">
            <input type="submit" value="Add" class="btn">
        </form>
    </div>
</template>


<script>
import uuid from 'uuid';
export default {
    name: "AddTodo",
    data() {
        return {
            title: ''
        }
    },
    methods: {
        addTodo() {
            e.preventDefault();
            const newTodo = {
                id: uuid.v4(),
                title: this.title,
                completed: false
            }
            this.$emit('add-todo', newTodo);
        }
    }
}
</script>
    name: "AddTodo"
<style scoped>
    form {
        display: flex;
    }

    input[type="text"] {
        flex: 10;
        padding: 5px;
    }

    input[type="submit"] {
        flex: 2;
    }
</style>
