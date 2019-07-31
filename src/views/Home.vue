<template>
    <div class="home">
        <h2>Form表单</h2>
        <k-form class="form" :model="form" :rules="rules">
            <k-form-item label="姓名" prop="username">
                <bar>
                    <k-input v-model="form.username"></k-input>
                </bar>
            </k-form-item>
            <k-form-item label="手机号" prop="mobile">
                <k-input v-model="form.mobile"></k-input>
            </k-form-item>
        </k-form>
    </div>
</template>

<script>
import Bar from "../components/bar";
import kForm from "../components/form/kForm";
import kFormItem from "../components/form/kFormItem";
import kInput from "../components/form/kInput";
export default {
    name: 'home',
    data() {
        return {
            form: {
                username: '',
                mobile: '',
            },
            rules: {
                username: [{ required: true, message: "姓名必填" }],
                mobile: [
                    { required: true, message: "手机号必填" },
                    { validator: (rule, value) => /^1\d{10}$/.test(value), message: "手机号不正确" }
                ]
            }
        }
    },
    components: {
        Bar,
        kForm,
        kFormItem,
        kInput
    },
    created() {
        console.log(this);
    }
}
</script>
<style lang="scss" scoped>
.vFormItem {
    margin-top: 10px;
}
</style>

