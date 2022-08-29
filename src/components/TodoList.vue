<template>
  <section class="todo-list">
    <ul>
      <li class="wrapper">
        <span class="index-label">No</span>
        <span class="item-text">item text</span>
        <span class="delete-button"></span>
      </li>
      <hr />
      <li class="wrapper" v-for="(todo, index) in todos" :key="index">
        <span class="index-label">{{ index + 1 }}</span>
        <span class="item-text">{{ todo }}</span>
        <button class="delete-button" @click="deleteItem(index)">delete</button>
      </li>
    </ul>
  </section>
</template>

<script lang="ts">
import { defineComponent, computed } from "vue";

export default defineComponent({
  props: {
    todos: Array,
  },
  emits: {
    update: (value: number) => true,
  },
  setup(props, context) {
    const todos = computed(() => props.todos);
    const deleteItem = (index: number) => {
      context.emit("update", index);
    };
    return {
      todos,
      deleteItem,
    };
  },
});
</script>

<style scoped>
.todo-list {
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
