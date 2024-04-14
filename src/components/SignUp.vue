<template>
    <img class="logo" src="../assets/images(vue).jpeg" alt="image">
    <h1>Sign Up</h1>
    <div class="register">
        <input type="text" v-model="name" placeholder="Enter Your Name">
        <input type="email" v-model="email" placeholder="Enter Your Email">
        <input type="password" v-model="password" placeholder="Enter Your Password">
        <button v-on:click="SignUp()">Sign Up</button>
    </div>
    <p><router-link to="/login">Log In</router-link></p>
</template>

<script>
import axios from 'axios';
export default {
    name: 'SignUp',
    data() {
        return {
            name: "",
            email: "",
            password: ""
        }
    },
    methods: {
        async SignUp() {
            console.warn("Sign Up Succesfully.", this.name, this.email, this.password);
            let result = await axios.post("http://localhost:3000/user", {
                name: this.name,
                email: this.email,
                password: this.password
            });
            console.warn(result);
            if (result.status == 201) {
                
                localStorage.setItem("user-info", JSON.stringify(result.data))
                this.$router.push({name:'Home'})
            }    
        }
    },
    mounted() {
        let user = localStorage.getItem('user-info');
        if (user) {
            this.$router.push({name:'Home'})
        }
    },
}
</script>

<style>

</style>