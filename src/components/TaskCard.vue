<template>
  <div :class="['task-card', { done }]">
    <div>
      <h3>{{ title }}</h3>
      <p>{{ description }}</p>
         <span class='right floated trash icon' v-on:click="deleteTask(task)">
      <i class='trash icon'> 🗑 </i>
    </span>
    </div>
    <Checkbox @click.native="$emit('toggle-task', taskIndex)" :checked="done" />
  </div>

</template>


<script>
import Checkbox from "./Checkbox";

export default {
  components: {
    Checkbox,
  },

  props: {
    title: String,
    description: String,
    done: Boolean,
    taskIndex: Number,
  },


methods: {
    deleteTask(task) {
      this.$emit('delete-task', task);
    },
  },

};
</script>

<style lang="scss">
.task-card {
  display: flex;
  text-align: left;
  background-color: saturate(rgba(#1e56a0, 0.03), 30%);
  transition: all 0.3s;
  min-height: 6rem;
  border-bottom: solid 1px rgba(#35495e, 0.1);
  border-left: solid 8px #1e56a0;
  p {
    font-size: 1.1rem;
  }
  &:hover {
    background-color: white;
    transform: scale(1.02);
    box-shadow: 2px 3px 10px rgba(black, 0.1);
  }
  & > div:first-child {
    margin: 0 1rem;
    padding: 1rem 0;
    flex-grow: 1;
    display: flex;
    flex-direction: column;
    justify-content: center;
  }
  &.done {
    border-left: solid 8px rgba(#35495e, 0.3);
    background-color: rgba(#35495e, 0.08);
    h3,
    p {
      text-decoration: line-through;
      opacity: 0.3;
    }
    &:hover {

      transform: unset;
      box-shadow: unset;
    }
  }
}
</style>
