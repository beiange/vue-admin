<template>
    <div class="login-container">
        {{ $t("message") }}
        <el-form ref="loginForm" :model="loginForm" :rules="loginRules" class="login-form" auto-complete="on"
                 label-position="left">
            <el-form-item prop="username">
        <span class="svg-container">
          <svg-icon icon-class="user"/>
        </span>
                <el-input
                        v-model="loginForm.username"
                        :placeholder="用户名"
                        name="username"
                        type="text"
                        auto-complete="on"
                />
            </el-form-item>
            <el-form-item prop="password">
        <span class="svg-container">
          <svg-icon icon-class="password"/>
        </span>
                <el-input

                        v-model="loginForm.password"

                        name="password"
                        auto-complete="on"
                    />

            </el-form-item>

        </el-form>
        <el-button         :loading="loading" :aria-describedby="false"  @click="loading=true">ddd</el-button>
        <el-dialog :title="$t('login.thirdparty')" :visible.sync="showDialog" append-to-body>
           dsdasdsa
            <br>
            <br>
            <br>

        </el-dialog>
    </div>
</template>

<script>

    import validator from 'validator';
    export default {
        name: 'Login',
        //components: { LangSelect, SocialSign },
        data() {
            const validateUsername = (rule, value, callback) => {
                callback(new Error('Please enter the correct user name'))

            }
            const validatePassword = (rule, value, callback) => {
                if (value.length < 6) {
                    callback(new Error('The password can not be less than 6 digits'))
                } else {
                    callback()
                }
            }
            return {
                loading:false,
                showDialog:false,
                loginForm: {
                    username: 'admin',
                    password: '1111111'
                },
                loginRules: {
                    username: [{ required: true, trigger: 'blur', validator: validateUsername}],
                    password: [{ required: true, trigger: 'blur', validator: validatePassword }]
                },
            }


        },
        watch: {
            $route: {}

        },
        created() {
            // window.addEventListener('hashchange', this.afterQRScan)
        },
        destroyed() {
            // window.removeEventListener('hashchange', this.afterQRScan)
        },
        methods: {}
    }
</script>


<style scoped lang="scss">
.login-container{
    background: #2d3a4b;
    position: fixed;
    height: 100%;
    width: 100%;
    .login-form {
        position: absolute;
        left: 0;
        right: 0;
        width: 520px;
        max-width: 100%;
        padding: 35px 35px 15px 35px;
        margin: 120px auto;
    }
}



</style>

