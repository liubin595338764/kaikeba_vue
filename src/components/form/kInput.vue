<template>
    <div class="kInput">
        <input type="text" class="input" :value="value" @input="onInput" v-bind="$attrs" />
    </div>
</template>

<script>
export default {
    name: 'kInput',
    inheritAttrs: false,
    props: {
        value: {
            type: String,
            default: ''
        }
    },
    methods: {
        onInput(e) {
            this.$emit('input', e.target.value);
        },
    },
}
</script>

<style lang="scss" scoped>
@import "~sass/variable.scss";
.kInput {
    width: 400px;
    input {
        padding: 0 10px;
        width: 100%;
        height: 33px;
        line-height: 1;
        background: #fff;
        border: 1px solid #dcdfe6;
        border-radius: 4px;
        transition: all 0.2s linear;
        box-sizing: border-box;
        outline: none;
        &:focus {
            border-color: $primary;
        }
    }
}
</style>