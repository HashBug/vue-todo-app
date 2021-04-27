<template>
  <form @submit="createTask">
    <label for="desc">Description</label>
    <input type="text" name="desc" v-model="desc" id="desc" />
    <label for="date">Date</label>
    <input type="text" name="date" v-model="date" id="date" />
    <label for="reminder">Reminder</label>
    <input type="checkbox" name="reminder" v-model="reminder" id="reminder" />
    <button type="submit" id="task-btn">Add Task</button>
  </form>
</template>

<script>
export default {
  name: "AddTask",
  data() {
    return {
      desc: "",
      date: "",
      reminder: false,
    };
  },
  methods: {
    createTask(e) {
      e.preventDefault();

      let newTask = {
        description: this.desc,
        date: this.date,
        reminder: this.reminder,
      };

      this.$emit("add-task", newTask);

      this.desc = "";
      this.date = "";
      this.reminder = false;
    },
  },
};
</script>

<style>
form {
  margin: 1em 0;
  background: #f4f4f4;
  padding: 0.8em;
  display: grid;
  grid-template-columns: 1fr;
  grid-gap: 0.5em;
  justify-content: start;
}
label {
  margin: 0.5em 0;
  justify-self: start;
}
input {
  height: 2em;
}

#reminder {
  width: 5%;
}

#task-btn {
  height: 2em;
  background: #202020;
  color: white;
}
</style>
