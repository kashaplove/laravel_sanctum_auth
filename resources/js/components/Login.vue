<template>
    <div class="w-25">
        <input v-model="email" type="email" placeholder="email" class="form-control mb-2 mt-3">
        <input v-model="password" type="password" placeholder="password" class="form-control mb-2">
        <input @click.prevent="login" type="submit" value="Login" class="btn btn-primary">
        <router-link :to="{ name: 'user.registration'}" class="btn btn-success">Registration</router-link>
    </div>
</template>

<script>
export default {
    name: "Login",
    data() {
        return {
            email: null,
            password: null,
        }
    },

    methods: {
        login() {
            axios.get('/sanctum/csrf-cookie')
                .then(response => {
                    axios.post('/login', {email: this.email, password: this.password})
                        .then(r => {
                            console.log(r);
                        })
                        .catch(err => {
                            console.log(err.response);
                        })
            })
        }
    }
}
</script>

<style scoped>

</style>
