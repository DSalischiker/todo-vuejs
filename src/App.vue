<template>
  <div id="app">
    <h1>ToDo List</h1>
    <!-- Components -->
    <Tasks :tasks="tasks"/>
    <TaskEntry :tasks="tasks"/>
  </div>
</template>

<script>
//imports
import TaskEntry from '@/components/TaskEntry.vue';
import Tasks from '@/components/Tasks.vue';
export default {
  name: 'App',
  data(){
    return{
      tasks: [
        'Primera tarea',
        'Segunda tarea',
        'Tercera tarea',
      ],
    }
  },
  components: {
    TaskEntry,
    Tasks,
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
