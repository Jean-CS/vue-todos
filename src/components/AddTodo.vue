<template>
  <div>
    <form @submit="addTodo">
      <div class="ui fluid action input">
        <input
          type="text"
          v-model="title"
          ref="title"
          name="title"
          placeholder="Add Todo..."
          autofocus
        >
        <button type="submit" class="ui button">Submit</button>
      </div>
    </form>
  </div>
</template>

<script>
import uuid from "uuid";

export default {
  name: "AddTodo",
  data() {
    return {
      title: ""
    };
  },
  methods: {
    addTodo(e) {
      e.preventDefault();

      // Prevents a user from adding an empty todo
      if (!this.title.trim()) {
        this.title = "";
        return false;
      }

      const newTodo = {
        id: uuid.v4(),
        title: this.title,
        completed: false
      };

      // Send up to parent
      this.$emit("add-todo", newTodo);

      // Resets the input text and sets focus to it
      this.title = "";
      this.$refs.title.focus();
    }
  }
};
</script>

<style scoped>
.ui.button {
    background-color: #41b88394;
}

.ui.button:hover {
    background-color: #41b883c2;
}
</style>


