<template>
  <div class="container">
    <header>
      Header
      <Button text="Add Task" color="green" />
    </header>
  </div>
</template>
<script>
import Button from "./Button";
export default {
  name: "Header",
  components: {
    Button,
  },
};
</script>

<style>
header {
  display: flex;
  justify-content: space-between;
  align-content: center;
  padding: 1em;
  border: 1px solid black;
}
</style>
