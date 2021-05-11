<template>
  <div class="tasks-container">
    <div class="filter-container">
      <button
        :class="{ selected: this.selected == 'all' }"
        value="all"
        @click="selected = $event.target.value"
      >
        All
      </button>
      <button
        :class="{ selected: this.selected == 'unfinished' }"
        value="unfinished"
        @click="selected = $event.target.value"
      >
        Unfinished
      </button>
      <button
        :class="{ selected: this.selected == 'finished' }"
        value="finished"
        @click="selected = $event.target.value"
      >
        Finished
      </button>
    </div>
    <ul class="tasks-list">
      <Task
        v-for="(task, index) in tasksToShow"
        :key="index"
        :task="task"
        @deleteTask="deleteTask"
        @finishedTask="finishedTask"
      />
    </ul>
    <!-- <p>To-do Tasks: {{ tasksUnfinished.length }}</p> -->
  </div>
</template>

<script>
import Task from "@/components/Task.vue";
export default {
  name: "Tasks",
  props: ["tasks"],
  data() {
    return {
      selected: "all",
    };
  },
  components: {
    Task,
  },
  methods: {
    deleteTask(task) {
      const taskId = this.tasks.indexOf(task);
      this.tasks.splice(taskId, 1);
    },
    finishedTask(task) {
      task.finished = !task.finished;
      /* this.tasks[index].finished = !this.tasks[index].finished; */
    },
  },
  computed: {
    tasksToShow() {
      if (this.selected == "all") {
        return this.tasks;
      } else if (this.selected == "unfinished") {
        return this.tasks.filter((task) => task.finished == false);
      } else {
        return this.tasks.filter((task) => task.finished == true);
      }
    },
  },
};
</script>

<style lang="scss" scoped>
div.tasks-container {
  width: 100%;
  padding: 0;
  margin: 0 auto;
  display: flex;
  flex-direction: column;
  background-color: #3a3a3a;
  border-radius: 4px;
}
div.filter-container {
  width: 90%;
  display: flex;
  justify-content: flex-start;
  margin: 1em auto 0 auto;
  align-items: center;
  gap: 1em;
  button {
    text-transform: uppercase;
    font-size: 10px;
    letter-spacing: 3px;
    font-weight: 800;
    border-radius: 4px;
    display: inline-block;
    border: none;
    padding: 0.5em 1.5em;
    margin: 0;
    height: 2.5em;
    background-color: #242424;
    color: #ebebeb;
    &:hover {
      background-color: #494949;
    }
    &.selected {
      background-color: #ebebeb;
      color: #242424;
    }
  }
}
.tasks-list {
  width: 90%;
  margin: 1em 0;
  display: flex;
  flex-direction: column;
  justify-content: center;
}
</style>
