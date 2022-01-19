<template>
  <fieldset>
    <div class="new-task">
      <legend>New task</legend>
      <div class="row">
        <label for="">Appointment name</label>
        <input v-model="text" type="text" />
      </div>
      <div class="row">
        <label for="">Date</label>
        <input v-model="day" type="date" />
      </div>
      <div class="row">
        <input v-model="reminder" type="checkbox" />
        <label for="">Reminder</label>
      </div>
    </div>
  </fieldset>
  <Button @btn-clicked="addNewTask()" :btnText="btnText" />
</template>

<script>
import Button from "./Button.vue";
export default {
  data() {
    return {
      btnText: "Ok",
      id: Math.random() * 10000,
      text: '',
      day: '',
      reminder: false,
    };
  },
  components: {
    Button,
  },
  methods: {
    addNewTask() {
      console.log("add new task");
      const newTask = {
        id: Math.random() * 10000,
        text: this.text,
        day: this.day,
        reminder: this.reminder,
      };
      console.log(newTask);
      this.$emit('addNewTask', newTask);

      this.text = '';
      this.day = '';
      this.reminder = '';
    },
  },
};
</script>

<style>
.new-task {
  display: flex;
  flex-direction: column;
  align-items: center;
  row-gap: 20px;
}

input,
label {
  display: block;
  text-align: left;
}
</style>
