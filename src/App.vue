<template>
  <div class="maincontent">
    <Header @btn-clicked="showNewTask" :headerName="headerName" :btnText="btnText" />
    <NewTask v-if="showNewTaskModal" @add-new-task="saveNewTask" />
    <Tasks @set-reminder="setReminder" @remove-task="deleteTask" class="taskscontainer" :tasks="tasks" />
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Tasks from "./components/Tasks.vue";
import NewTask from './components/NewTask.vue';

export default {
  name: "App",
  data() {
    return {
      headerName: "Task tracker",
      btnText: "Show form",
      tasks: [],
      showNewTaskModal: false,
    };
  },
  components: {
    Header,
    Tasks,
    NewTask,
  },
methods: {
  deleteTask(id) {
    console.log('ka trinam: ', id);
    const index = this.tasks.findIndex(el => el.id === id);
    this.tasks.splice(index, 1);
    console.log(this.tasks.length)
  },
  saveNewTask(task) {
    this.tasks.push(task);
  },
  showNewTask() {
    this.showNewTaskModal = !this.showNewTaskModal;
  },
  setReminder(id) {
    const index = this.tasks.findIndex(el => el.id === id);
    this.tasks[index].reminder = !this.tasks[index].reminder;
  }
},

  created() {
    this.tasks = [
      {
        id: 1,
        text: "Doctor appointment",
        day: "Appril Monday 10 AM",
        reminder: true,
      },
      {
        id: 2,
        text: "Visit dantist",
        day: "June Thursday 10 AM",
        reminder: false,
      },
      {
        id: 3,
        text: "Job interview",
        day: "July Friday 10 AM",
        reminder: true,
      },
    ];
  },
};
</script>

<style scoped>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.maincontent {
  margin: 60px 0;
  width: 500px;
  text-align: center;
  border: 1px solid rgb(190, 187, 187);
  border-radius: 10px;
}

.taskscontainer {
  margin: 60px 0;
}
</style>
