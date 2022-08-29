<template>
  <section class="todo-input-content">
    <label for="input-value">input item text</label>
    <input
      class="todo-input"
      type="text"
      id="input-value"
      v-model="state.inputValue"
    />
    <button class="add-button" @click="addItem">add</button>
  </section>
</template>

<script lang="ts">
import { defineComponent, reactive } from "vue";

interface State {
  inputValue: string;
}

export default defineComponent({
  emits: {
    update: (value: string) => true,
  },
  setup(_, context) {
    const state = reactive<State>({
      inputValue: "",
    });
    const addItem = () => {
      context.emit("update", state.inputValue);
      state.inputValue = "";
    };
    return {
      state,
      addItem,
    };
  },
});
</script>

<style scoped>
.todo-input-content {
  margin-top: 32px;
  text-align: end;
}
.todo-input {
  margin-left: 4px;
}
.add-button {
  width: 120px;
  margin-left: 4px;
}
</style>
