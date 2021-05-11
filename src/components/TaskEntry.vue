<template>
  <div id="taskentry-container">
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

<style lang="scss" scoped>
#taskentry-container {
  display: flex;
  justify-content: space-between;
  gap: 0.5em;
}
input {
  width: 75%;
  padding: 12px 20px;
  margin: 0.5em 0 0.5em 0;
  display: inline-block;
  border: 0;
  border-radius: 4px;
  box-sizing: border-box;
  font-size: 14px;
}
button {
  width: 25%;
  padding: 12px 20px;
  display: inline-block;
  margin: 0.5em 0 0.5em 0;
  border: 0;
  border-radius: 4px;
  box-sizing: border-box;
  background-color: #53d647;
  color: #ebebeb;
  font-weight: 800;
  text-transform: uppercase;
  font-size: 10px;
  letter-spacing: 3px;
}
</style>
