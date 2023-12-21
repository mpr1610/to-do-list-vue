<template>
  <div class="tasks-grid">
    <template v-if="tasks.length">
      <ComponentsTask
        v-for="(task, i) in tasks"
        :key="task.name"
        :task="task"
        @taskDeleted="$emit('taskDeleted', i)"
        @taskStateChanged="$emit('taskStateChanged', i)"
      ></ComponentsTask>
    </template>
    <p v-else class="no-task">Sua vida está em dia :)</p>
  </div>
</template>

<script>
import ComponentsTask from "./ComponentsTask.vue";

export default {
  props: {
    tasks: { type: Array, required: true },
  },
  components: { ComponentsTask },
};
</script>

<style scoped>
.tasks-grid {
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
}

.tasks-grid .task {
  margin: 10px;
}

.no-task {
  color: #aaa;
  font-size: 1.7rem;
}
</style>
