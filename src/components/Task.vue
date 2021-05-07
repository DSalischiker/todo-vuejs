<template>
  <div>
    <li>{{ task.title }} | Finished: {{ task.finished }}</li>
    <div id="buttons">
      <button @click="$emit('deleteTask')">Delete</button>
      <button @click="$emit('finishedTask')">Done</button>
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
  methods: {},
};
</script>

<style lang="scss" scoped>
div {
    max-width: 800px;
    margin: 0 auto;
    display: flex;
    justify-content: space-between;
  li {
      padding: 1em;
      text-align: left;
    list-style: none;
  }
  #buttons{
      padding: 1em;
      display: flex;
      justify-content: flex-end;
  }
}
</style>
