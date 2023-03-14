<template>
  <div class="container text-start bg-light shadow-sm my-2 p-2 rounded">
    <div class="row">
      <div class="col">
        <h5>{{ title }}</h5>
        <hr />
      </div>
    </div>
    <div class="row align-items-end">
      <div class="col">
        <p>{{ task }}</p>
      </div>
    </div>
    <div class="row justify-content-around">
      <div class="col-auto">
        <button @click="remove()" type="button" class="btn btn-danger">
          Remove <font-awesome-icon icon="fa-solid fa-circle-minus" />
        </button>
      </div>
      <div v-if="done" class="col-auto">
        <button @click="setUndone()" type="button" class="btn btn-secondary">
          Undone <font-awesome-icon icon="fa-solid fa-circle-check" />
        </button>
      </div>
      <div v-else class="col-auto">
        <button @click="setDone()" type="button" class="btn btn-success">
          Done <font-awesome-icon icon="fa-solid fa-circle-check" />
        </button>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "ListItem",
  props: {
    title: String,
    task: String,
    index: Number,
    done: { type: Boolean, default: false },
  },
  emits: ["done", "undone", "remove"],
  methods: {
    setDone(): void {
      this.$emit("done", this.index);
    },
    setUndone(): void {
      this.$emit("undone", this.index);
    },
    remove(): void {
      this.$emit("remove", this.index);
    },
  },
});
</script>
