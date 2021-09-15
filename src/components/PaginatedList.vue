<template>
  <ul>
    <li v-for="el in currentWindow" :key="el.id">
      {{ el.content }}
    </li>
  </ul>
</template>

<script>
export default {
  props: {
    items: {
      type: Array,
    },
    limit: {
      type: Number,
    },
    offset: {
      type: Number,
    },
  },
  computed: {
    currentWindow() {
      return this.items.slice(this.offset, this.limit);
    },
  },
};
</script>

<style></style>
