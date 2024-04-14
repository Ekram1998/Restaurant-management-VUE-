<template>
    <img class="logo" src="../assets/images(vue).jpeg" alt="image">
    <h1>Log In</h1>
    <div class="login">
        <input type="email" v-model="email" placeholder="Enter Your Email">
        <input type="password" v-model="password" placeholder="Enter Your Password">
        <button v-on:click="login()">Log In</button>
    </div>
    <p><router-link to="/sign-up">Sign Up</router-link></p>
</template>

<script>
import axios from 'axios';
export default {
    name: 'LogIn',
    data() {
        return {
            email: '',
            password: ''
        }
    },
    methods: {
        async login() {
            let result = await axios.get(
                `http://localhost:3000/user?email=${this.email}&password=${this.password}`
            );
            if (result.status == 200 && result.data.length>0) {
                localStorage.setItem('user-info', JSON.stringify(result.data[0]));
                this.$router.push({name:'Home'})
            }
            // console.warn('login done',result);
        }
    },
    mounted() {
        let user = localStorage.getItem('user-info');
        if (user) {
            this.$router.push({ name:'Home'})
        }
    }
}
</script>