<template>
  <ToDoInput @update="addItem"></ToDoInput>
  <section class="item-content">
    <ul>
      <li class="wrapper">
        <span class="index-label">No</span>
        <span class="item-text">item-detail</span>
        <span class="delete-button"></span>
      </li>
      <hr />
      <li class="wrapper" v-for="(todo, index) in state.todos" :key="index">
        <span class="index-label">{{ index + 1 }}</span>
        <span class="item-text">{{ todo }}</span>
        <button class="delete-button" @click="deleteItem(index)">delete</button>
      </li>
    </ul>
  </section>
</template>

<script lang="ts">
import { defineComponent, reactive } from "vue";

import ToDoInput from "./ToDoInput.vue";

interface State {
  todos: Array<string>;
}

export default defineComponent({
  components: {
    ToDoInput,
  },
  setup() {
    const state = reactive<State>({
      todos: ["text A", "text B", "text C"],
    });
    const addItem = (item: string) => {
      state.todos = [...state.todos, item];
    };
    const deleteItem = (index: number) => {
      state.todos.splice(index, 1);
    };
    return {
      state,
      addItem,
      deleteItem,
    };
  },
});
</script>

<style scoped>
.add-item-content {
  margin-top: 32px;
  text-align: end;
}
.add-item-input {
  margin-left: 4px;
}
.add-button {
  width: 120px;
  margin-left: 4px;
}

.item-content {
  margin-top: 24px;
}

.wrapper {
  display: flex;
}

.wrapper:nth-child(n + 2) {
  margin-top: 8px;
}
.index-label {
  flex: 0.1;
}
.item-text {
  flex: 0.7;
}
.delete-button {
  flex: 0.2;
}
</style>
