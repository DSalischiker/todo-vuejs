<template>
  <div class="tasks-container">
    <div class="filter-container">
      <button value="all" @click="selected = $event.target.value">
        All
      </button>
      <button value="unfinished" @click="selected = $event.target.value">
        Unfinished
      </button>
      <button value="finished" @click="selected = $event.target.value">
        Finished
      </button>
    </div>
    <br />
    <span>{{ selected }}</span>
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
  width: 50%;
  margin: 0 auto;
  display: flex;
  flex-direction: column;
  background-color: #dfecf5;
  border-radius: 20px;
}
div.filter-container{
width: 80%;
display: flex;
justify-content: flex-start;
margin: 1em auto 0 auto;
align-items: center;
gap: 1em;
}
.tasks-list{
    width: 80%;
    margin: 1em auto;
    display: flex;
    flex-direction: column;
    justify-content: center;
}
</style>
