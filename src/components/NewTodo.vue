<template>
  <div class="form-container">
    <md-field class="input-field">
      <label>Task</label>
      <md-input v-model="task" @keyup.enter="handleSubmit"></md-input>
    </md-field>
    <md-button class="md-accent input-button" @click="handleSubmit"
      >Add Task</md-button
    >
  </div>
</template>
<script>
import { v4 as uiv4 } from "uuid";
export default {
  name: "NewTodo",
  data: () => ({
    task: "",
  }),
  methods: {
    handleSubmit(e) {
      e.preventDefault();
      const newTodo = { id: uiv4(), task: this.task, done: false };
      this.$emit("add-todo", newTodo);
      this.task = "";
    },
  },
};
</script>
<style scoped>
.input-field,
.input-button,
.form-container {
  display: flex;
}
.form-container {
  padding: 1rem;
  align-items: center;
  justify-content: space-between;
}
</style>
