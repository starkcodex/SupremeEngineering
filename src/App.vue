

<template>
  <div id="wrapper">
    <nav class="navbar is-light">
      
      <div class="navbar-brand">
          <router-link to="/" class="navbar-item"><strong>SupremeEng</strong></router-link>
      </div>

        <div class="navbar-menu">
          <div class="navbar-end">
              <template v-if="$store.state.isAuthenticated">
                <router-link to="/dashboard" class="navbar-item">Dashboard</router-link>
                <router-link to="/dashboard/clients" class="navbar-item">Clients</router-link>

                <div class="navbar-item">
                    <div class="buttons">
                      <router-link to="/dashboard/my-account" class="button is-dark">My Account</router-link>
                    </div>
                </div>

              </template>

              <template v-else>
                <router-link to="/home" class="navbar-item">Home</router-link>

                <div class="navbar-item">
                  <div class="buttons">
                    <router-link to="/sign-up" class="button is-warning"> <strong>Sign up</strong></router-link>
                    <router-link to="/log-in" class="button is-light"> <strong>Log in</strong></router-link>
                  </div>
                </div>

              </template>
          </div>
        </div>
      </nav>
  
    <section class="section">
      <router-view/>
    </section>


    <footer class="footer">
        <p class="has-text-centered"><strong>Copyright</strong> (c) 2024 Inc</p>
        <p class="has-text-centered"> Marfley Technologies.</p>
    </footer>
  </div>
</template>


<script>

import axios from 'axios';


  export default {
    name: 'App',
    beforeCreate() {
      this.$store.commit('initializeStore')
      const token  = this.$store.state.token

      if (token) {
        axios.defaults.headers.common['Authorization'] = "Token " + token
      } else {
        axios.defaults.headers.common['Authorization'] = ""
      }

    }
  }
</script>



<style lang="scss">

/* @import '../node_modules/bulma'; */
@import './../node_modules/bulma/css/bulma.css';

</style>
