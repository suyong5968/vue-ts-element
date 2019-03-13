<!--  -->
<template>
    <div class="login-container">
        <el-form class="login-form" autoComplete="on" :model="loginForm" :rules="loginRules" ref="loginForm"
                 label-position="left">
            <h3 class="title">iyuedian-admin</h3>
            <el-form-item prop="loginAccount">
        <span class="svg-container svg-container_login">
          <i class="el-icon-service"></i>
            <!-- <svg-icon icon-class="user" /> -->
        </span>
                <el-input name="loginAccount" type="text" v-model="loginForm.loginAccount" autoComplete="on"
                          placeholder="username"/>
            </el-form-item>
            <el-form-item prop="password">
        <span class="svg-container svg-container_login">
          <i class="el-icon-rank"></i>
            <!-- <svg-icon icon-class="password"/> -->
        </span>
                <el-input name="password" type="password" @keyup.enter.native="handleLogin()"
                          v-model="loginForm.password" autoComplete="on"
                          placeholder="password"></el-input>
            </el-form-item>
            <el-form-item>
                <el-button type="primary" style="width:100%;" :loading="loading" @click.native.prevent="handleLogin()">
                    Sign in
                </el-button>
            </el-form-item>
        </el-form>
    </div>
</template>


<script lang="ts">
    import {Component, Vue} from "vue-property-decorator";

    interface Validate {
        loginAccount: string;
        password: string;
    }

    @Component
    export default class Login extends Vue {
        // name: "login";
        private loading: boolean = false;

        private loginForm: Validate = {
            loginAccount: "",
            password: "",
        };

        created() {
            console.log("ok");
        }
    };
</script>

<!--vue组件中的style标签有scoped属性时，表明css样式只适用于当前组件元素-->
<style rel="stylesheet/scss" lang="scss" scoped>
    $bg: #2d3a4b;
    $dark_gray: #889aa4;
    $light_gray: #eee;
    .login-container {
        position: fixed;
        height: 100%;
        width: 100%;
        background-color: $bg;

        .login-form {
            position: absolute;
            left: 0;
            right: 0;
            width: 520px;
            padding: 35px 35px 15px 35px;
            margin: 120px auto;
        }

        .tips {
            font-size: 14px;
            color: #fff;
            margin-bottom: 10px;

            span {
                &:first-of-type {
                    margin-right: 16px;
                }
            }
        }

        .svg-container {
            padding: 6px 5px 6px 15px;
            color: $dark_gray;
            vertical-align: middle;
            width: 40px;
            display: inline-block;

            &_login {
                font-size: 20px;
            }
        }

        .title {
            font-size: 26px;
            font-weight: 400;
            color: $light_gray;
            margin: 0px auto 40px auto;
            text-align: center;
            font-weight: bold;
        }

        .show-pwd {
            position: absolute;
            right: 10px;
            top: 7px;
            font-size: 16px;
            color: $dark_gray;
            cursor: pointer;
            user-select: none;
        }
    }
</style>
