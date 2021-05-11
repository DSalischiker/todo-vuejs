<template>
  <div>
    <li :class="{'task-finished': task.finished}">{{ task.title }}</li>
    <div class="buttons-container">
      <button class="delete" @click="deleteTask">
        <FontAwesomeIcon id="delete_icon" :icon="['fas', 'trash-alt']" />
      </button>
      <button class="finished" @click="finishedTask">
        <FontAwesomeIcon v-if="!task.finished" id="unfinished_icon" :icon="['fas', 'check']" />
        <FontAwesomeIcon v-if="task.finished" id="finished_icon" :icon="['fas', 'times']" />
      </button>
    </div>
  </div>
</template>

<script>
import { library } from "@fortawesome/fontawesome-svg-core";
import { FontAwesomeIcon } from "@fortawesome/vue-fontawesome";
import { faTrashAlt, faCheck, faTimes } from "@fortawesome/free-solid-svg-icons";

library.add(faTrashAlt, faCheck, faTimes);
export default {
  name: "Task",
  components: {
    FontAwesomeIcon,
  },
  props: ["task"],
  data() {
    return {};
  },
  methods: {
    deleteTask() {
      this.$emit("deleteTask", this.task);
    },
    finishedTask() {
      this.$emit("finishedTask", this.task);
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
    width: 70%;
    padding: 1em 1em 1em 0;
    list-style: none;
    text-align: left;
    &.task-finished{
      text-decoration: line-through;
      color: #8f8f8f;
    }
  }
  div.buttons-container {
    max-width: 30%;
    padding: 0.5em;
    display: flex;
    justify-content: flex-end;
    align-items: center;
    gap: 0.5em;
    button {
      width: 3.5em;
      display: inline-block;
      border: none;
      padding: 0.5rem 1rem;
      margin: 0;
      text-decoration: none;
      font-weight: 600;
      border-radius: 4px;
      /* padding: 0.1em 1em; */
      height: 2.5em;
      background-color: #242424;
      &:hover {
        background-color: #494949;
      }
      #delete_icon {
        color: #e43838;
      }
      #unfinished_icon {
        color: #53d647;
      }
      #finished_icon {
        color: #ebebeb;
      }
    }
  }
}
</style>
