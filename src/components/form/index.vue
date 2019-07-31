<template>
    <div class="kForm">
        <slot></slot>
    </div>
</template>

<script>
export default {
    props: {
        model: {
            type: Object,
            required: true
        },
        rules: {
            type: Object,
            default: {}
        },
    }
}
</script>

<style lang="scss" scoped>
@import "~sass/variable.scss";
</style>