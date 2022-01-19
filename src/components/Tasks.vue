<template>
  <div class="tasks">
    <Task @set-reminder="$emit('setReminder', task.id)" @remove-task="$emit('removeTask', task.id)" :key="task.id" v-for="task in tasks" :task="task" :reminder="task.reminder" />
  </div>
</template>

<script>
import Task from "./Task.vue";

export default {
    props: ['tasks', 'reminder'],
    components: {
        Task,
    }
}
</script>

<style scoped>
.tasks {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  row-gap: 20px;
}
</style>
