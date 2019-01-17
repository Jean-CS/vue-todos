<template>
  <div class="todo-item item">
    <div class="ui checkbox left floated content">
      <input type="checkbox" v-on:change="markComplete">
      <label v-bind:class="{'is-complete': todo.completed}">{{todo.title}}</label>
    </div>
    <button class="circular ui red right floated icon button mini del" @click="$emit('del-todo', todo.id)">
        <i class="icon trash"></i>
    </button>
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
};
</script>

<style scoped>
.is-complete {
  text-decoration: line-through;
}

/* .del {
  background: #ff0000;
  color: #fff;
  border: none;
  padding: 5px 9px;
  border-radius: 50%;
  cursor: pointer;
  float: right;
} */
</style>

