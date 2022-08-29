<template>
  <TodoInput @update="addItem"></TodoInput>
  <TodoList :todos="state.todos" @update="deleteItem"></TodoList>
</template>

<script lang="ts">
import { defineComponent, reactive } from "vue";

import TodoInput from "./TodoInput.vue";
import TodoList from "./TodoList.vue";

interface State {
  todos: Array<string>;
}

export default defineComponent({
  components: {
    TodoInput,
    TodoList,
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

<style scoped></style>
