<template>
  <div class="todolist-container">
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
          title: "Lorem ipsum dolor sit amet, consectetur adipiscing elit.",
          finished: false,
        },
        {
          title: "Vestibulum vitae libero nec metus dapibus rutrum ut vel est.",
          finished: true,
        },
        {
          title: "Sed pharetra diam quis arcu semper, ac facilisis elit vestibulum.",
          finished: false,
        },
        {
          title: "Integer varius nunc quis luctus tincidunt.",
          finished: true,
        },
        {
          title: "Phasellus a nunc non ligula iaculis sollicitudin.",
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

<style lang="scss">
.todolist-container{

  width: 80%;
  max-width: 800px;
  margin: 0 auto;
}
button{
  cursor: pointer;
}
</style>
