<template>
  <div>
    <span v-for="r in repetitions" :key="r">
      {{ content }}
    </span>
  </div>
</template>

<script>
export default {
  props: ["times", "content"],
  /*   props: {
    config: {
      type: Object,
      validator(value) {
        return (
          typeof value.times === "number" && typeof value.content === "string"
        );
      },
    },
  }, */

  computed: {
    repetitions() {
      return Array.from({ length: this.times });
    },
  },
};
</script>

<style></style>
