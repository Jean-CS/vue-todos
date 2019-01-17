<template>
    <div>
        <form @submit="addTodo">
            <input type="text" v-model="title" ref="title" name="title" placeholder="Add Todo..." autofocus>
            <input type="submit" value="Submit" class="btn">
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
        addTodo(e) {
            e.preventDefault();

            // Prevents a user from adding an empty todo
            if (!this.title.trim()) {
                this.title = '';
                return false;
            }

            const newTodo = {
                id: uuid.v4(),
                title: this.title,
                completed: false 
            }

            // Send up to parent
            this.$emit('add-todo', newTodo);

            // Resets the input text and sets focus to it
            this.title = '';
            this.$refs.title.focus();
        }
    }
}
</script>

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


