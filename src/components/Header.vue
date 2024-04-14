<template>
    <div class="nav">
        <router-link to="/">Home</router-link>
        <router-link to="add">Add Restaurent</router-link>
        <!-- <router-link to="update">Update Restaurent</router-link> -->
        <a v-on:click="logout" href="#">LogOut</a>
    </div>
</template>

<script>
export default {
    // eslint-disable-next-line vue/multi-word-component-names
    name: 'Header',
    methods: {
        logout() {
            console.log("Logout.");
            // clear localstorage
            localStorage.clear();
            // page return redirect other page
            this.$router.push({name:'LogIn'})
        }
    },
}
</script>

<!-- custom style -->
<style>
.nav{
    background-color: #333;
    overflow: hidden;
    padding: 10px;
}
.nav a{
    float: left;
    color: #f2f2f2;
    text-align: center;
    padding: 10px 14px;
    text-decoration: none;
    font-size: 16px;
    margin-right: 4px;
}
.nav a:hover{
    background-color: #ddd;
    color: #222;
}
</style>