<template>
    <button @click="$emit('btnClicked')">{{ btnText }}</button>
</template>

<script>
export default {
    name: 'Button',
    data() {
        return {
        }
    },
    props: ['btnText'],
}
</script>

<style>
    button {
        height: 35px;
        background: lightgreen;
        border: 0;
        padding: 0 15px;
    }
</style>