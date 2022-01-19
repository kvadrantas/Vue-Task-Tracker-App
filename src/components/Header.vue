<template>
    <div>
        <h1>{{ headerName }} </h1>
        <Button @btn-clicked="$emit('btnClicked')" :btnText="btnText" />
    </div>
</template>

<script>
import Button from "./Button.vue";
export default {
    name: 'Header',
    components: {
        Button,
    },
    props: ['headerName', 'btnText'],
}
</script>

<style type="scss" scoped>
    div {
        display: flex;
        flex-direction: row;
        justify-content: center;
        align-items: center;
        column-gap: 70px;
    }
</style>