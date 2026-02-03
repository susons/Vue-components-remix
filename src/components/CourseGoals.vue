<template>
  <ul>
    <li v-for="goal in goals" :key="goal">
      <slot :item="goal"></slot>
    </li>
  </ul>
</template>

<script>
export default {
  components: {},
  data() {
    return {
      goals: ["Learn cooking", "learn carrot cakes"],
    };
  },
};
</script>

<style></style>
