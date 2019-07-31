<template>
    <div class="home">
        <img alt="Vue logo" src="../assets/logo.png" />
        <k-form-item label="姓名">
            <k-input v-model="form.username"></k-input>
        </k-form-item>
        <p>{{form.username}}</p>
        <!-- <HelloWorld msg="Welcome to Your Vue.js App" /> -->
    </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'
import kFormItem from "../components/form/kFormItem";
import kInput from "../components/form/kInput";
export default {
    name: 'home',
    data() {
        return {
            form: {
                username: ''
            }
        }
    },
    components: {
        kFormItem,
        kInput
    },
}
</script>
