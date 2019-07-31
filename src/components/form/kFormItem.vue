<template>
    <div class="vFormItem">
        <label v-if="label">{{label}}</label>
        <slot></slot>
        <p class="error" v-if="error">{{error}}</p>
    </div>
</template>

<script>
export default {
    props: {
        label: String
    }
}
</script>

<style lang="scss" scoped>
@import "~sass/variable.scss";
.error {
    color: $error;
}
</style>