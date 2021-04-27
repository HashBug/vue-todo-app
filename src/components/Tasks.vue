<template>
  <div class="tasks">
    <div :key="task.id" v-for="task in tasks">
      <Task
        :task="task"
        @toggle-reminder="$emit('toggle-reminder', task.id)"
        @delete-task="$emit('delete-task', task.id)"
      />
    </div>
  </div>
</template>

<script>
import Task from "./Task";
export default {
  name: "Tasks",
  components: {
    Task,
  },
  props: {
    tasks: Array,
  },
};
</script>

<style></style>
