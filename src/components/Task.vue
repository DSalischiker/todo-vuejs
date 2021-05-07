<template>
  <div>
    <li>{{ task }}</li>
    <button>Delete</button>
    <button>Done</button>
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

<style lang="scss" scoped></style>
