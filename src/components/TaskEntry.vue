<template>
  <div>
    <input
      v-model="newTask"
      type="text"
      @keyup.prevent="keymonitor"
      placeholder="Ingrese una tarea"
    />
    <button type="submit" @click="addTask">Agregar Tarea</button>
  </div>
</template>

<script>
export default {
  name: "TaskEntry",
  props: ["tasks"],
  data() {
    return {
      newTask: "",
    };
  },
  methods: {
    addTask() {
      if (this.newTask != "") {
        this.tasks.push({
          title: this.newTask,
          finished: false,
        });
        this.newTask = "";
      }
    },
    keymonitor: function(event) {
      console.log(event.key);
      if (event.key == "Enter") {
        this.addTask();
      }
    },
  },
};
</script>

<style lang="scss" scoped></style>
