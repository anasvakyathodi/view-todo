<template>
  <md-list-item>
    <md-checkbox v-on:change="handleCheck" :value="!this.item.done" />
    <span v-if="this.item.done" class="md-list-item-text"
      ><s>{{ this.item.task }}</s></span
    >
    <span v-else class="md-list-item-text">{{ this.item.task }}</span>
    <md-button class="md-icon-button md-accent" @click="handleClick(item.id)">
      <md-icon>close</md-icon>
    </md-button>
  </md-list-item>
</template>
<script>
export default {
  props: ["item"],
  methods: {
    handleCheck() {
      this.item.done = !this.item.done;
    },
    handleClick(id) {
      console.log("clicked");
      this.$parent.$parent.$parent.handleDelete(id);
    },
  },
};
</script>
