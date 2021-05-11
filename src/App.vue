<template>
  <div id="app">
    <h1>ToDo List</h1>
    <!-- Components -->
    <ToDoList/>
  </div>
</template>

<script>
import ToDoList from '@/components/ToDoList.vue';
export default {
  name: "App",
  components: {
    ToDoList,
  },
};
</script>

<style lang="scss">
body{
  background-color: #242424;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #e6e6e6;
  background-color: #242424;
  margin-top: 60px;
}
</style>
