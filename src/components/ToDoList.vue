<template>
  <div>
    <Tasks :tasks="tasks" />
    <TaskEntry :tasks="tasks" />
  </div>
</template>

<script>
//imports
import TaskEntry from "@/components/TaskEntry.vue";
import Tasks from "@/components/Tasks.vue";
export default {
  name: "ToDoList",
  data() {
    return {
      tasks: [
        {
          title: "1",
          finished: false,
        },
        {
          title: "2",
          finished: true,
        },
        {
          title: "3",
          finished: false,
        },
        {
          title: "4",
          finished: true,
        },
        {
          title: "5",
          finished: false,
        },
      ],
    };
  },
  components: {
    TaskEntry,
    Tasks,
  },
};
</script>

<style lang="scss" scoped></style>
