<template>
  <div class="container">
    <TaskHeader
      title="Task-Tracker"
      @AddTaskToggle="toggleAddTask"
      :showAddTaskP="showAddTask"
    />
    <div v-show="showAddTask">
      <AddTask @newTask="addTask" />
    </div>
    <TaskComp
      :task="tasks"
      @delete-task="deleteTask"
      @toggle-reminder="toggleRemainder"
    />
  </div>
</template>

<script>
import TaskHeader from "./components/TaskHeader.vue";
import TaskComp from "./components/TaskComp.vue";
import AddTask from "./components/AddTask.vue";
import axios from "axios";
export default {
  name: "App",
  components: {
    TaskHeader,
    TaskComp,
    AddTask,
  },
  data() {
    return {
      tasks: [],
      showAddTask: false,
    };
  },

  methods: {
    async deleteTask(id) {
      console.log("task id ===>", id);
      const res = await axios.delete(`http://localhost:3000/tasks/${id}`);
      console.log("res", res);
      if (res.status == 200) {
        this.tasks = this.tasks.filter((task) => {
          return task.id !== id;
        });
      }

    },
    toggleRemainder(id) {
      console.log("Hello", id);
      this.tasks = this.tasks.map((item) =>
        item.id === id ? { ...item, reminder: !item.reminder } : item
      );
    },

    toggleAddTask() {
      this.showAddTask = !this.showAddTask;
    },

    async addTask(task) {
      const res = await fetch("http://localhost:3000/tasks", {
        method: "POST",
        headers: {
          "Content-type": "application/json",
        },
        body: JSON.stringify(task),
      });
      const data = await res.json();

      this.tasks = [...this.tasks, data];
    },
    async getTask() {
      const res = await axios.get("http://localhost:3000/tasks");
      console.log("data==>", res.data);
      return res.data;
    },
  },

  async created() {
    this.tasks = await this.getTask();
   
  },
};
</script>

<style></style>
