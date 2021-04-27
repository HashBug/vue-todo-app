<template>
  <div
    @dblclick="$emit('toggle-reminder', task.id)"
    :class="[task.reminder ? 'reminder' : '', 'task']"
  >
    <p class="desc">
      {{ task.description }}
      <span
        ><i @click="$emit('delete-task', task.id)" class="fas fa-times"></i
      ></span>
    </p>
    <p class="date">{{ task.date }}</p>
  </div>
</template>

<script>
export default {
  name: "Task",
  props: {
    task: Object,
  },
  methods: {},
};
</script>

<style>
.task {
  background: #f4f4f4;
  padding: 0.5rem;
  margin: 0.8em 0;
  position: relative;
}

.reminder .desc::before {
  content: "";
  width: 0.5em;
  height: 100%;
  position: absolute;
  left: 0;
  top: 0;
  background: green;
}

.desc {
  display: flex;
  justify-content: space-between;
  padding: 0 0.5em;
}

.desc i {
  color: red;
  cursor: pointer;
}

.date {
  display: flex;
  font-style: italic;
  font-size: 0.8rem;
  padding: 0 0.5em;
}
</style>
