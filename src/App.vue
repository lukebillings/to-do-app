<template>
  <div id="app">
    <img alt="Task icon" src="./assets/task.svg" height="150">
    <h1>Tasky</h1>
    <p>Don't keep it in your head. Pop it down in a task...</p>
    <TasksList />
  </div>
</template>

<script>
import TasksList from './components/TasksList.vue';

export default {
  name: 'App',
  components: {
    TasksList
  }
};
</script>


<style lang="scss">
@import "./assets/style.scss";
</style>
