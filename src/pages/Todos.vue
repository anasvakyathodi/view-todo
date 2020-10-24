<template>
  <div class="page-container">
    <md-list v-if="this.todos.length">
      <md-subheader>Tasks</md-subheader>
      <div v-bind:key="item.id" v-for="item in todos">
        <TodoItem :item="item" />
      </div>
    </md-list>
    <md-empty-state
      v-if="!this.todos.length"
      class="md-accent"
      md-rounded
      md-icon="assignment_turned_in"
      md-label="No Tasks"
      md-description="Create a new task and it will show up here."
    >
    </md-empty-state>
  </div>
</template>

<script>
import TodoItem from "./../components/TodoItem";
export default {
  name: "Todos",
  components: {
    TodoItem,
  },
  props: ["todos"],
};
</script>

<style scoped>
.md-list {
  vertical-align: top;
  border: 1px solid rgba(#000, 0.12);
}
.container {
  max-width: 720px;
  width: 100%;
  margin: auto;
}
.md-empty-state {
  margin: 2rem auto;
  max-width: 80%;
  height: 80%;
}
</style>
