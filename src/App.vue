<template>
  <div id="app">
    <img alt="Task icon" src="./assets/task.svg" height="200">
    <h1>Tasky</h1>
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
