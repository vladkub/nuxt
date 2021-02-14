<template>
  <section class="container">
    <div>
      <logo/>
      <h1 class="title">
        nuxt-express 
      </h1>
      <h2 class="subtitle">
        My mind-blowing Nuxt.js project
      </h2>
      <button v-on:click="greet">Add</button>
      <div class="links">
        <p>{{ info.data }}</p>
        <a href="https://nuxtjs.org/" target="_blank" class="button--green">Documentation</a>
        <a href="https://github.com/nuxt/nuxt.js" target="_blank" class="button--grey">GitHub</a>
      </div>
    </div>
  </section>
</template>

<script>
import Logo from '~/components/Logo.vue'
import axios from 'axios'

export default {
  components: {
    Logo
  },
  data() {
    return {
      info: []
    }
  },
  methods: {
    greet: function (event) {
      this.$axios.post( '/api/users', {
          name: 'Vlad',
          age: 29
        })
    }
  },
  mounted() {
    axios
      .get('http://localhost:3000/api/users')
      .then(response => (this.info = response));
    console.log(this.info);
  }
}
</script>

<style>
.container
{
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}
.title
{
  font-family: "Quicksand", "Source Sans Pro", -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif; /* 1 */
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}
.subtitle
{
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}
.links
{
  padding-top: 15px;
}
</style>
