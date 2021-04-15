<template>
  <div id="app">
    <p>You clicked {{ numOfClicks }} times.</p>
    <button @click="handleClick()">Click me to increment!</button>
  </div>
</template>

<script>
import { ref } from "vue";

export default {
  name: "IncrementCompositionAPI",
  setup() {
    let numOfClicks = ref(0);

    function handleClick() {
      numOfClicks.value++;
    }

    return {
      handleClick,
      numOfClicks,
    };
  },
};
</script>

<style>

</style>
