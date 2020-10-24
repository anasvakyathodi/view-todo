<template>
  <div id="app">
    <md-progress-spinner
      v-if="!loaded"
      class="md-accent"
      :md-diameter="30"
      md-mode="indeterminate"
    ></md-progress-spinner>
    <div v-if="loaded">
      <Header />
      <NewTodo v-on:add-todo="handleData" />
      <Todos :todos="todos" v-on:del-todo="handleDelete" />
    </div>
  </div>
</template>

<script>
import Vue from "vue";
import VueMaterial from "vue-material";
import "vue-material/dist/vue-material.min.css";
import "vue-material/dist/theme/default-dark.css"; // This line here

Vue.use(VueMaterial);

// components
import Todos from "./pages/Todos.vue";
import Header from "./components/Header.vue";
import NewTodo from "./components/NewTodo.vue";
export default {
  mounted() {
    this.loaded = true;
    console.log("App Mounted");
    if (localStorage.getItem("todo_items"))
      this.todos = JSON.parse(localStorage.getItem("todo_items"));
  },
  name: "App",
  components: {
    Todos,
    Header,
    NewTodo,
  },
  data() {
    return {
      todos: [],
      loaded: false,
    };
  },
  methods: {
    handleDelete(id) {
      this.todos = this.todos.filter((todo) => todo.id !== id);
    },
    handleData(data) {
      this.todos = [...this.todos, data];
    },
  },
  watch: {
    todos: {
      handler() {
        console.log("Todo Items array changed!");
        localStorage.setItem("todo_items", JSON.stringify(this.todos));
      },
      deep: true,
    },
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
.md-progress-spinner {
  position: absolute;
  left: 0;
  right: 0;
  margin-top: 5rem;
  margin-left: auto;
  margin-right: auto;
  width: fit-content;
}
</style>
