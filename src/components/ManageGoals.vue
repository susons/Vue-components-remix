<template>
  <div>
    <h2>Manage goals</h2>
    <input ref="goal" type="text" />
    <button @click="setGoal">Set goal</button>
    <teleport to="#app">
      <ErrorAlert v-if="inputError"
        ><h2>input is invalid</h2>
        <p>Enter some goal you want to achive</p>
        <button @click="inputError = false">Close</button></ErrorAlert
      >
    </teleport>
  </div>
</template>

<script>
import ErrorAlert from "./ErrorAlert.vue";

export default {
  components: {
    ErrorAlert,
  },
  data() {
    return {
      inputError: false,
    };
  },
  methods: {
    setGoal() {
      const value = this.$refs.goal.value;

      if (!value) {
        this.inputError = true;
      }
    },
  },
};
</script>
