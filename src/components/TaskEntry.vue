<template>
  <div>
    <input v-model="newTask" type="text" placeholder="Ingrese una tarea" />
    <button type="submit" @click="addTask">Agregar Tarea</button>
  </div>
</template>

<script>
export default {
  name: "TaskEntry",
  props: ['tasks'],
  data() {
    return {
      newTask: "",
    };
  },
  methods: {
    addTask() {
        this.tasks.push(this.newTask);
        this.newTask = '';
    },
  },
};
</script>

<style lang="scss" scoped></style>
