<template>
    <button @click="$emit('click', $event)">
        {{ title }}
    </button>
</template>

<script>
    export default {
        name: "Button",
        props: {
            title: String
        }
    }
</script>

<style lang="scss" scoped>
    button {
        border: none;
        font-size: 1em;
        cursor: pointer;
        font-weight: 600;
        max-width: 150px;
        padding: 20px 56px;
        border-radius: 4px;
        width: max-content;
        background-color: #60e3a1;
        white-space: nowrap;
    }
</style>