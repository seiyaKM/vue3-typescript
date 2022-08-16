<script lang="ts">
import { defineComponent, reactive } from "vue";

export default defineComponent({
  setup() {
    const state = reactive({
      todos: ["text A", "text B", "text C"],
    });
    return {
      state,
    };
  },
});
</script>

<template>
  <section>
    <label for="add-text">add item text</label>
    <input type="text" id="add-text" />
    <button>add</button>
  </section>
  <section>
    <label for="delete-text">select delete items</label>
    <button>delete</button>
  </section>
  <section>
    <ul>
      <li v-for="todo in state.todos" :key="index"></li>
    </ul>
  </section>
</template>

<style scoped></style>
