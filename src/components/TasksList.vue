<template>
  <div id="tasks">
    <p>This is my first Vue.js component</p>
    <div v-if="tasks.length" class="tasks-list">
      <TaskCard
        v-for="(task, index) in tasks"
        :key="index"
        :title="task.title"
        :description="task.description"
        :done="task.done"
      />

    </div>

    <p v-else-if="!newFormVisible">You don't have any tasks yet...</p>
  </div>
</template>

<script>
import TaskCard from './TaskCard';

export default {
  name: 'TasksList',
  components: {
    TaskCard
  },


data() {
  return {
    tasks: [
      {
        title: "Create a card component",
        description:
          "Create a new TaskCard.vue file in the components folder, then import it in TasksList",
        done: true,
      },
      {
        title: "Make the card component dynamic",
        description:
          "Learn about using the data option and passing data to child components using props",
        done: true,
      },
      {
        title: "Bind the attributes to the data",
        description:
          "Use the v-bind directive to bind the title and description to our data",
        done: false,
      },
    ],
  };
 },
};
</script>


