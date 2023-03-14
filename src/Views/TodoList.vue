<template>
  <div class="container text-start">
    <div class="row">
      <div class="col">
        <NewItem @add="handleAdd($event)" />
      </div>
    </div>
    <div class="row justify-content-center">
      <h4>Todo:</h4>
      <hr />
      <p v-if="todoList.length === 0" class="text-center">
        There is nothing here..
      </p>
      <div
        class="col-12 col-md-6 col-lg-4"
        v-for="(todoItem, index) in todoList"
        :key="`list-item-${index}`"
      >
        <ListItem
          :title="todoItem.title"
          :task="todoItem.task"
          :index="index"
          @done="handleDone($event)"
          @remove="handleRemove(todoList, $event)"
        />
      </div>
    </div>
    <div class="row justify-content-center">
      <h4>Done:</h4>
      <hr />
      <p v-if="completeList.length === 0" class="text-center">
        There is nothing here..
      </p>
      <div
        class="col-12 col-md-6 col-lg-4"
        v-for="(todoItem, index) in completeList"
        :key="`list-item-${index}`"
      >
        <ListItem
          :title="todoItem.title"
          :task="todoItem.task"
          :index="index"
          :done="true"
          @undone="handleUndone($event)"
          @remove="handleRemove(completeList, $event)"
        />
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import ListItem from "@/components/ListItem.vue";
import NewItem from "@/components/NewItem.vue";

type form = { title: string; task: string };

export default defineComponent({
  name: "TodoList",
  data() {
    return {
      todoList: [] as form[],
      completeList: [] as form[],
    };
  },
  components: {
    ListItem,
    NewItem,
  },
  methods: {
    handleAdd(newItem: form): void {
      this.todoList.push(newItem);
    },
    handleRemove(list: form[], index: number): void {
      list.splice(index, 1);
    },
    handleDone(index: number): void {
      this.completeList.push(this.todoList[index]);
      this.handleRemove(this.todoList, index);
    },
    handleUndone(index: number): void {
      this.todoList.push(this.completeList[index]);
      this.handleRemove(this.completeList, index);
    },
  },
});
</script>
