<template>
  <div>
    <li>{{ task.title }}</li>
    <div class="buttons-container">
      <button @click="deleteTask">Delete</button>
      <button @click="finishedTask">Done</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "Task",
  props: ["task"],
  data() {
    return {};
  },
  methods: {
    deleteTask(){
      this.$emit('deleteTask', this.task);
    },
    finishedTask(){
      this.$emit('finishedTask', this.task);
    },
  },
};
</script>

<style lang="scss" scoped>
div {
    width: 100%;
    display: flex;
    justify-content: flex-start;
  li {
      padding: 1em 1em 1em 0;
      font-weight: 600;
      list-style: none;
  }
  div.buttons-container{
      padding: 1em;
      display: flex;
      justify-content: flex-end;
      gap: 1em;
  }
  div.buttons-container>button{
    background-color: #ecf2f7;
    font-weight: 600;
    border-radius: 8px;
    border: 2px solid white;
    padding: 0.5em 1em;
    &:hover{
      background-color: #cce4f5;
    }
  }
}
</style>
