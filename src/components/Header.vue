<template>
    <v-toolbar dark class="cyan">
        <v-toolbar-title class="mr-4">
            <span @click="navigateTo('/')" class="header"> Song Tracker </span>
        </v-toolbar-title>

        <v-toolbar-items>
            <v-btn flat dark :to="{'name': 'songs'}">Browse</v-btn>
        </v-toolbar-items>

        <v-spacer></v-spacer>

        <v-toolbar-items v-if="!$store.state.isUserLoggedIn">
            <v-btn flat dark :to="{'name': 'login'}">Login</v-btn>
        </v-toolbar-items>

        <v-toolbar-items v-if="!$store.state.isUserLoggedIn">
            <v-btn flat dark :to="{'name': 'register'}">Sign Up</v-btn>
        </v-toolbar-items>

        <v-toolbar-items v-if="$store.state.isUserLoggedIn">
            <v-btn flat dark @click="logout()">Log Out</v-btn>
        </v-toolbar-items>
    </v-toolbar>
</template>

<script>
export default {

    methods: {
        navigateTo (route){
            this.$router.push(route)
        },
        logout (){
            this.$store.dispatch('setToken', null)
            this.$store.dispatch('setUser', null)
            this.$router.push({name: 'root'})
        }
    }
    
}
</script>

<style scoped>
.header {
    cursor: pointer;
}
</style>
