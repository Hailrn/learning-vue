<template>
    <div v-if="!login" class="login" id="login">
        <h1 :class="{hovered : hovered}">LOGIN PAGE</h1>
        <div :class="['form' ,{appear : hovered}]">
            <div class="secondary-container">
                <span class="errorMsg">Username atau password salah. Silakan coba lagi.</span>
                <div class="input-container username-container">
                    <input v-model="username" type="text" class="formInput" id="username">
                    <label for="username" class="label">Username</label>
                </div>
                
                <div class="input-container password-container">
                    <input v-model="password" type="password" class="formInput" id="password">
                    <label for="password" class="label">Password</label>
                </div>
                <button @click="Login" class="login-btn btn" id="login-btn">Login!</button>
            </div>
        </div>
    </div>
    <div v-else class="greeting" id="greeting">
        <div class="container-greeting">
            <span class="greeting-msg" id="greetingMsg">Selamat datang, {{ status }}! Anda memiliki akses {{ status === "Admin" ? "penuh" : "terbatas" }}.</span>
            <button @click="Logout" class="logout-btn btn" id="logout-btn">Logout!</button>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'LoginForm',
        data() {
            return {
                login : false,
                username : "",
                password : "",
                status : ""
            }
        },
        props: {
            hovered : String
        },
        methods: {
            Login(){
                if (this.username === "admin" && this.password === "1234") {
                    document.getElementById("login").classList.add("break-content")
                    setTimeout(() => {
                        this.username = ""
                        this.password = ""
                        this.status = "Admin"
                        this.login = true
                        setTimeout(() => {
                            document.getElementById("greeting").classList.add("appear")
                        }, 200);
                    }, 700)
                } else if (this.username === "user" && this.password === "abcd") {
                    document.getElementById("login").classList.add("break-content")
                    setTimeout(() => {
                        this.status = "Pengguna"
                        this.login = true
                        setTimeout(() => {
                            document.getElementById("greeting").classList.add("appear")
                        }, 200);
                    }, 700)
                } else {
                    this.WrongCredentials()
                }
            },
            WrongCredentials() {
                document.querySelector(".secondary-container").classList.add("scroll-down")
                setTimeout(() => document.querySelector(".errorMsg").classList.add("appear"), 300)
            },
            Logout() {
                document.getElementById("greeting").classList.add("break-content")
                setTimeout(() => {
                    this.status = ""
                    this.login = false
                }, 700)
            }
        },
        watch: {
            username(newVal) {
                if (newVal !== "") {
                    document.getElementById("username").classList.add("isValued")
                } else {
                    document.getElementById("username").classList.remove("isValued")
                }
            },
            password(newVal) {
                if (newVal !== "") {
                    document.getElementById("password").classList.add("isValued")
                } else {
                    document.getElementById("password").classList.remove("isValued")
                }
            }
        }
    }
</script>

<style scoped>
    .login {
        transition: all 0.7s ease;
    }
    h1 {
        transition: all 1s ease;
        transform: translateY(100px);
        margin: 15px 0;
    }
    .hovered {
        transform: translateY(10px);
    }
    .form{
        height: 190px;
        transform: translateX(-60px);
        opacity: 0;
        transition: 1s all ease;
        overflow: hidden;
    }
    .secondary-container {
        height: 100%;
        display: flex;
        flex-direction: column;
        flex-wrap: wrap;
        align-items: center;
        justify-content: space-around;
        transform: translateY(-30px);
        transition: all 0.7s ease;
    }
    .scroll-down {
        transform: translateY(0px);
    }
    .errorMsg {
        opacity: 0;
        transform:translateX(-30px);
        transition: all 0.7s ease;
        color: rgb(143, 0, 0);
    }
    .input-container {
        width: 60%;
        display: flex;
    }
    .input-container input{
        margin-left: 33px;
    }
    .formInput {
        background-color: transparent;
        border-top: none;
        border-left: none;
        border-right: none;
        border-bottom: 2px solid black;
    }
    .formInput:focus {
        outline: none;
    }
    .label{
        font-weight: bold;
        display: inline-block;
        transform: translateX(-170px) translateY(-4px);
        transition: 0.5s all;
    }
    .label:hover {
        cursor: text;
    }
    .formInput:focus + .label,
    .formInput.isValued + .label{
        transform: translateX(-170px) translateY(-20px);
    }
    .btn {
        all: unset;
        cursor: pointer;
        width: 100px;
        height: 30px;
        border-radius: 15px;
        position: relative;
        z-index: 2;
        overflow: hidden;
        font-weight: bold;
        transition: all 1s ease;
    }
    .login-btn{
        border: solid rgb(91, 69, 213) 2px;
        color: rgb(137, 122, 255);
    }
    .logout-btn{
        border: solid rgb(171, 0, 0) 2px;
        color: rgb(218, 0, 0);
    }
    .btn::before{
        content: "";
        width: 120px;
        height: 120px;
        position: absolute;
        border-radius: 50%;
        top: 100%;
        left: 70%;
        z-index: -1;
        transition: all 0.7s ease;
    }
    .login-btn::before{
        background-color: rgb(137, 122, 255);
    }
    .logout-btn::before{
        background-color: rgb(218, 0, 0);
    }
    .btn:hover::before{
        top: -100%;
        left: -8%;
    }
    .btn:hover{
        color: white;
    }
    .greeting {
        display: flex;
        justify-content: center;
        align-items: center;
        height: 100%;
        width: 100%;
        opacity: 0;
        transform: translateX(-40px);
        transition: all 0.7s ease;
    }
    .container-greeting{
        display: flex;
        flex-direction: column;
        flex-wrap: wrap;
        align-items: center;
        justify-content: space-around;
        width: 80%;
        height: 40%;
    }
    .greeting-msg{
        font-size: 22px;
    }
    .appear {
        transform: translateX(0px);
        opacity: 1;
    }
    .break-content {
        transform: translateX(-30px);
        opacity: 0;
    }
</style>