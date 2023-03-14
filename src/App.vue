<template>
  <h2 class="mb-4"><span class="text-vue-green">Vue</span> Basics Demo</h2>
  <h4>Todo List</h4>
  <TodoList />
</template>

<script lang="ts">
import { defineComponent } from "vue";
import TodoList from "./Views/TodoList.vue";

export default defineComponent({
  name: "App",
  components: {
    TodoList,
  },
});
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.text-vue-green {
  color: #42b883;
}
</style>
