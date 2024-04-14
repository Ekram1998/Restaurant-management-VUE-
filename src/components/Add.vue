<template>
    <Header/>
    <h1>Hello User, Welcome On Add Page</h1>
    <form class="add">
        <input type="text" name="name" placeholder="Input Restaurant Name" v-model="restaurant.name">
        <input type="text" name="address" placeholder="Input Restaurant Address" v-model="restaurant.address">
        <input type="text" name="contact" placeholder="Input Contact Number" v-model="restaurant.contact">
        <button type="button" v-on:click="addRestaurant">Add New Restaurant</button>
    </form>
</template>

<script>
import axios from 'axios'
import Header from './Header.vue'
export default {
    // eslint-disable-next-line vue/multi-word-component-names
    name: 'Add',
    components: {
        Header
    },
    data() {
        return {
            restaurant: {
                name: '',
                address: '',
                contact: ''
            }
        }
    },
    methods: {
        async addRestaurant() {
            let result = await axios.post("http://localhost:3000/restaurant", {
                name: this.restaurant.name,
                address: this.restaurant.address,
                contact: this.restaurant.contact,
            })
            if (result) {
                this.$router.push({ name: 'Home' })
            }
        },
    },
    mounted() {
        let user = localStorage.getItem('user-info');
        if (!user) {
            this.$router.push({name:'login'})
        }
    },
}
</script>