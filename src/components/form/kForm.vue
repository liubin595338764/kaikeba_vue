<template>
    <div class="kForm">
        <slot></slot>
    </div>
</template>

<script>
export default {
    provide() {
        return {
            form: this
        }
    },
    props: {
        model: {
            type: Object,
            required: true
        },
        rules: {
            type: Object,
        },
    },
    methods: {
        validate(callback) {
            const list = this.$children
                .filter(item => item.prop)
                .map(item => item.validate());

            Promise.all(list)
                .then(() => callback && callback(true))
                .catch(() => callback && callback(false));
        }
    },
}
</script>

<style lang="scss" scoped>
@import "~sass/variable.scss";
</style>