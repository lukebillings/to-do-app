<template>
  <div id="tasks">
    <p>This is my first Vue.js component</p>
    <TaskCard />
  </div>
</template>

<script>
import TaskCard from './TaskCard';

export default {
  name: 'TasksList',
  components: {
    TaskCard
  }
};
</script>
