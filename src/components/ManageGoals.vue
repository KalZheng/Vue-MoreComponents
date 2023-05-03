<template>
  <div>
    <h2>Manage Gaols</h2>
    <input type="text" ref="goal" />
    <button @click="setGoal">Set Goal</button>
    <!-- issue with this is that it is under the button in html in 
        browser inspect might cause css error -->
        <!-- hence we use teleport to move to outside -->
    <teleport to="body" >
        <error-alert v-if="inputIsInvalid">
          <h2>Input is invalid</h2>
          <p>Please Enter atleast a few characters...</p>
          <button @click="confirmError">Okay</button>
        </error-alert>
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
      inputIsInvalid: false,
    };
  },
  methods: {
    setGoal() {
      // will use the ref concept
      const enteredValue = this.$refs.goal.value;
      if (enteredValue === "") {
        // alert("input cannot be empty");
        this.inputIsInvalid = true;
      }
    },
    confirmError() {
      this.inputIsInvalid = false;
    },
  },
};
</script>
