<template>
    <Header/>
    <h1>Hello User, Welcome On Update Page</h1>
    <form class="add">
        <input type="text" name="name" placeholder="Input Restaurant Name" v-model="restaurant.name">
        <input type="text" name="address" placeholder="Input Restaurant Address" v-model="restaurant.address">
        <input type="text" name="contact" placeholder="Input Contact Number" v-model="restaurant.contact">
        <button type="button" v-on:click="UpdateRestaurant">Restaurant Update</button>
    </form>
</template>

<script>
import axios from 'axios';
import Header from './Header.vue'
export default {
    // eslint-disable-next-line vue/multi-word-component-names
    name: 'Update',
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
        async UpdateRestaurant() {
            let result = await axios.put("http://localhost:3000/restaurant/"+this.$route.params.id, {
                name: this.restaurant.name,
                address: this.restaurant.address,
                contact:this.restaurant.contact,
            })
            if (result.status == 200) {
                this.$router.push({ name: 'Home' })
            }
        },
    },
    async mounted() {
        let user = localStorage.getItem('user-info');
        if (!user) {
            this.$router.push({name:'login'})
        }
        let result = await axios.get("http://localhost:3000/restaurant/"+this.$route.params.id)
        // console.warn(result.data)
        this.restaurant = result.data
    },
}
</script>