<template>
  <div id="app">
    <ApiConfig base-url="https://jsonplaceholder.typicode.com" />
    <ApiConfig name="reqres" base-url="https://reqres.in/api/" />
    <Api url="/users/1" @success="x => user = x" />
    <Api name="reqres" url="/users" @success="x => users = x" />

    Logged in as {{ user.name }}

    <div id="nav">
      <router-link to="/">
        Home
      </router-link> |
      <router-link to="/about">
        About
      </router-link>
    </div>
    <router-view />
  </div>
</template>

<script>
import ApiConfig from '@/components/ApiConfig.vue';
import Api from '@/components/Api.vue';

export default {
  components: {
    Api,
    ApiConfig
  },

  data() {
    return {
      user: {},
      users: null
    };
  }
};

</script>

<style>
body {
  font-family: sans-serif;
}
</style>
