<template>
  <div class="topnav">
    <div class="navbar">
      <div>
        <nuxt-link to="/">Home</nuxt-link>
        <nuxt-link to="/blog">Blog</nuxt-link>
        <nuxt-link to="/about">About</nuxt-link>
        <nuxt-link to="/photos">Photo</nuxt-link>
        <nuxt-link to="/profile">Profile</nuxt-link>
      </div>
      <div>
        <nuxt-link to="/login">Login</nuxt-link>
      </div>
      <div v-if="loggedIn" class="buttons">
        <button @click="logout" class="button is-danger">
          <strong>Log Out</strong>
        </button>
      </div>
    </div>


  </div>
</template>
<script>
import { mapState } from 'vuex'

export default {
  data() {
    return {
      showNav: false,
    }
  },
  methods: {
    async logout() {
      await this.$auth.logout()

      this.$router.push('/login')
    },
  },
  computed: {
    ...mapState('auth', ['loggedIn']),
  },
}
</script>

<style>
.navbar {
  display: flex;
  justify-content: space-between;
}

.topnav {
  overflow: hidden;
  background-color: #04AA6D;
}

.topnav a {
  float: left;
  color: #f2f2f2;
  text-align: center;
  padding: 14px 16px;
  text-decoration: none;
  font-size: 17px;
}

.topnav a:hover {
  background-color: #ddd;
  color: black;
}

.topnav a.active {
  background-color: #04AA6D;
  color: white;
}
</style>
