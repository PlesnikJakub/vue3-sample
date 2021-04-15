<template>
  <div>
    <p>You clicked {{ numOfClicks }} times.</p>
    <button @click="handleClick()">Click me to increment!</button>
  </div>
</template>

<script>
export default {
  name: "IncrementOptionAPI",
  data() {
    return {
      numOfClicks: 0,
    };
  },
  created() {},
  methods: {
    handleClick: function () {
      this.numOfClicks++;
    },
  },
};
</script>

<style>

</style>
