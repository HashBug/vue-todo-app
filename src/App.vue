<template>
  <div id="app">
    <Header />
    <AddTask @add-task="addTask" />
    <Tasks
      :tasks="tasks"
      @delete-task="deleteTask"
      @toggle-reminder="toggleReminder"
    />
  </div>
</template>

<script>
import Header from "./components/Header";
import Tasks from "./components/Tasks";
import AddTask from "./components/AddTask";
export default {
  name: "App",
  components: {
    Header,
    Tasks,
    AddTask,
  },
  data() {
    return {
      tasks: [],
    };
  },
  methods: {
    deleteTask(id) {
      this.tasks = this.tasks.filter((task) => task.id !== id);
    },
    toggleReminder(id) {
      this.tasks = this.tasks.map((task) =>
        task.id === id ? { ...task, reminder: !task.reminder } : task
      );
    },
    addTask(task) {
      this.tasks = [task, ...this.tasks];
    },
  },
  created() {
    this.tasks = [
      {
        id: 1,
        description: "Meeting with client",
        reminder: true,
        date: "April 28 at 7:30pm",
      },
      {
        id: 2,
        description: "Open ICICI Account",
        reminder: true,
        date: "April 27 at 10:30am",
      },
      {
        id: 3,
        description: "Fix Outlook issue",
        reminder: false,
        date: "April 28 at 12:30pm",
      },
    ];
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  width: 50%;
  margin: 0 auto;
}
</style>
