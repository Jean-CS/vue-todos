<template>
  <header class="ui center aligned icon header">
    <h1>
      <img class="icon" alt="Vue logo" src="../../assets/logo.png">
      Todo List
    </h1>
    <div id="nav" class="ui horizontal list link">
      <router-link to="/" class="item" exact-active-class="active">Home</router-link>|
      <router-link to="/about" class="item" exact-active-class="active">About</router-link>
    </div>
  </header>
</template>

<script>
export default {
  name: "Header"
};
</script>

<style scoped>
.header {
  color: #fff;
  text-align: center;
  padding: 10px;
}

.header a {
  padding-right: 5px;
  text-decoration: none;
}
</style>
