<template>
  <div class="page-container">
    <md-app md-waterfall md-mode="fixed">
      <md-app-toolbar class="md-accent">
        <span class="md-title">Vue Todo</span>
      </md-app-toolbar>
    </md-app>
  </div>
</template>

<style scoped>
.md-app {
  max-height: 400px;
  border: 1px solid rgba(#000, 0.12);
}
.md-drawer {
  width: 230px;
  max-width: calc(100vw - 125px);
}
</style>

<script>
export default {
  name: "Header",
};
</script>
