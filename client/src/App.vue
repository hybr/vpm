<template>
  <div>
    <div id="app">
      <router-view></router-view >
    </div>
  </div>
</template>

<script>
import auth from './auth'

export default {

  name: 'App',

  data: () => {
    return {
      user: auth.user
    }
  },

  methods: {
    logout(){
      auth.logout(this, { headers: auth.getAuthHeader() })
    }
  }
}
</script>

<style>
@import url(https://cdnjs.cloudflare.com/ajax/libs/materialize/0.98.0/css/materialize.min.css);
</style>
