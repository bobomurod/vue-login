<template>
    <div id="login">
        <h1>Login<h1>
            <input type="text" name="username" v-model="input.username" placeholder="Username" />
            <input type="password" v-model="input.password" placeholder="Password" />
            <button type="button" v-on:click="login()">Login</button>
    </div>
</template>

<script>
export default {
    name: 'Login',
    data() {
        return {
            input: {
                username: "",
                password: ""
            }
        }
    },
    methods: {
        login() {
            if(this.input.username != "" && this.input.password != "") {
                if (this.input.username == this.$parent.mockAccount.username && this.input.password == this.$parent.mockAccount.password) {
                    this.$emit("authenticated", true);
                    this.$router.replace({name: "secure"});
                } else {
                    console.log("This username and password is incorrrect");
                }
            } else {
                console.log("A username and password must be present");
            }
        }
    }
}
</script>

<style scoped>
    #login {
        width: 500px;
        border: 1px solid #cccccc;
        background-color: bisque;
        margin: auto;
        margin-top: 200px;
        padding: 20px;
    }
</style>


