<template>
  <button class="btn" :style="{ background: color }" @click="onClick()">
    {{ text }}
  </button>
</template>

<script>
export default {
  name: "Button",
  props: {
    text: String,
    color: String,
  },
  data() {
    return {};
  },
  methods: {
    onClick() {
      console.log("button clicked");
    },
  },
};
</script>

<style>
.btn {
  padding: 0.5rem;
  border: 2px solid white;
  color: white;
}
.btn:hover {
  color: green;
  background: white !important;
  border: 2px solid green;
  cursor: pointer;
}
</style>
