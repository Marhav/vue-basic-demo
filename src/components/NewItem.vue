<template>
  <div class="container text-start bg-light shadow-sm my-3 p-2 rounded">
    <div class="row">
      <div class="col">
        <h4>New item</h4>
      </div>
    </div>
    <form class="row align-items-end" @submit.prevent="submit()">
      <div class="col mb-2">
        <div class="form-group">
          <label for="itemTitle">Title</label>
          <input
            v-model="title"
            type="text"
            class="form-control"
            id="itemTitle"
            aria-describedby="Enter title"
            placeholder="Enter title..."
            required
          />
        </div>
      </div>
      <div class="col-auto mb-2">
        <button type="submit" class="btn btn-primary">
          Add <font-awesome-icon icon="fa-solid fa-circle-plus" />
        </button>
      </div>
      <div class="col-12">
        <div class="form-group">
          <label for="itemTask">Task</label>
          <textarea
            v-model="task"
            type="text"
            class="form-control"
            id="itemTask"
            aria-describedby="Enter task"
            placeholder="Enter task..."
            required
          />
        </div>
      </div>
    </form>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "NewItem",
  data() {
    return { title: "" as string, task: "" as string };
  },
  emit: ["add"],
  methods: {
    submit(): void {
      this.$emit("add", { title: this.title, task: this.task });
      this.title = "";
      this.task = "";
    },
  },
});
</script>
