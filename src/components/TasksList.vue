<template>
  <div>
    <button class="btn round-icon" @click="newFormVisible = !newFormVisible">
      {{ newFormVisible ? "✕" : "＋" }}
    </button>

    <NewTask v-if="newFormVisible" @add-task="addTask" />

    <div v-if="tasks.length" class="tasks-list">
      <TaskCard
        v-for="(task, index) in tasks"
        :key="index"
        :title="task.title"
        :description="task.description"
        :done="task.done"
        :task-index="index"
        @toggle-task="toggleTask"
        v-on:delete-task="deleteTask"
        v-bind:todo="todo"
      />
      <a href="#" @click="resetTasks()" class="reset-link">Reset tasks</a>
    </div>

    <p v-else-if="!newFormVisible">No tasks today?</p>
  </div>
</template>

<script>
import TaskCard from "./TaskCard";
import NewTask from "./NewTask";
export default {

  name: "TasksList",
  components: {
    TaskCard,
    NewTask,
  },

  data() {
    return {
      tasks: JSON.parse(localStorage.getItem("tasks")) || [],
      newFormVisible: false,
    };
  },
  watch: {
    tasks() {
      localStorage.setItem("tasks", JSON.stringify(this.tasks));
    },
  },


  methods: {
    addTask(title, description, done = false) {
      this.tasks.unshift({ title, description, done });
      this.newFormVisible = false;
    },

    toggleTask(taskIndex) {
      const audio = new Audio(require('./sound-effect.mp3'));
      audio.play();
      const taskToUpdate = this.tasks[taskIndex];
      taskToUpdate.done = !taskToUpdate.done;
      this.$set(this.tasks, taskIndex, taskToUpdate);
    },


    resetTasks() {
      localStorage.setItem("tasks", null);
      this.tasks = [];
    },


    deleteTask(task) {
      const taskIndex = this.tasks.indexOf(task);
      this.tasks.splice(taskIndex, 1);
    },

  },


};
</script>

