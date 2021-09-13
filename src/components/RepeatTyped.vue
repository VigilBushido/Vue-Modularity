<template>
  <div>
    <span v-for="r in repetitions" :key="r">
      {{ content }}
    </span>
  </div>
</template>

<script>
export default {
  props: {
    times: {
      type: Number,
    },
    content: {
      value: "no-number-here",
      type: String,
    },
  },
  computed: {
    repetitions() {
      return Array.from({ length: this.times });
    },
  },
};
</script>

<style></style>
