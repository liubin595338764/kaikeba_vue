<template>
    <div class="vFormItem">
        <label v-if="label" class="formLabel">{{label}}</label>
        <slot></slot>
        <p class="error" v-if="error">{{error}}</p>
    </div>
</template>

<script>
import AsyncValidator from 'async-validator';
let unwatch;
export default {
    inject: ['form'],
    props: {
        label: String,
        prop: String
    },
    data() {
        return {
            error: ''
        }
    },
    mounted() {
        const feild = this.prop;
        unwatch = this.$watch(`form.model.${feild}`, () => {
            this.validate();
        });
    },
    beforeDestroy() {
        unwatch && unwatch();
    },
    methods: {
        validate() {
            const feild = this.prop;
            if (!feild) return true;
            const rule = this.form.rules[feild];
            const value = this.form.model[feild];
            const desc = {
                [feild]: rule
            }
            const v = new AsyncValidator(desc);
            return v.validate({ [feild]: value }, errors => {
                if (errors) {
                    this.error = errors[0].message;
                } else {
                    this.error = '';
                }
            })
        }
    },
}
</script>

<style lang="scss" scoped>
@import "~sass/variable.scss";
.formLabel {
    display: inline-block;
    margin-bottom: 5px;
}
.error {
    color: $error;
}
</style>