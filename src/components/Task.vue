<template>
    <div 
    class="task"
    :class="{active: reminder}"
    @dblclick="$emit('setReminder', task.id)"
    >
        <h3>{{ task.text }}</h3>
        <p>{{ task.day }}</p>
        <button @click="$emit('removeTask', task.id)">Delete</button>
    </div>
</template>

<script>
export default {
    props: ['task', 'reminder'],
}
</script>

<style scoped>
    .task {
        width: 80%;
        border: 1px solid grey;
        border-radius: 10px;
        background: rgb(235, 232, 232);
    }

    .active {
        border-left: 7px solid green;
    }

    h3, p {
        margin: 0;
        padding: 0;
        line-height: 30px;
    }
</style>