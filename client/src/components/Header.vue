<template>
  <v-toolbar fixed color='primary'>
    <v-toolbar-title class="white--text">
        <span
          class ="home"
          @click="navigateTo({name: 'root'})">
          Tab Tracker
        </span>
    </v-toolbar-title>
    <!-- ADD LATER
    <v-toolbar-items>
        <v-btn flat dark>
        Browse
        </v-btn>
    </v-toolbar-items> -->
    <v-btn flat dark
    @click="navigateTo({name: 'songs'})">
    Browse
    </v-btn>
    <v-spacer></v-spacer>
    <v-toolbar-items>
        <v-btn flat dark
        v-if="!$store.state.isUserLoggedIn"
        @click="navigateTo({name: 'login'})">
        Login
        </v-btn>

        <v-btn flat dark
        v-if="!$store.state.isUserLoggedIn"
        @click="navigateTo({name: 'register'})">
        Sign Up
        </v-btn>

        <v-btn flat dark
        v-if="$store.state.isUserLoggedIn"
        @click="logout">
        Log Out
        </v-btn>
    </v-toolbar-items>
  </v-toolbar>
</template>

<script>
export default {
  methods: {
    navigateTo (route) {
      this.$router.push(route)
    },
    logout () {
      this.$store.dispatch('setToken', null)
      this.$store.dispatch('setUser', null)
      this.$router.push({
        name: 'root'
      })
    }
  }
}
</script>

<style scoped>
.home {
    cursor: pointer;
}
</style>
