<template>
  <div class="container">
    <div>
      <logo />
      <h1 class="title">
        This is the final Title
      </h1>
      <h2 class="subtitle">
        My bedazzling Nuxt.js NEW project # {{  envVar }} #
      </h2>
      <div class="links">
        <a href="https://nuxtjs.org/" target="_blank" class="button--green">
          Awesome Documentation
        </a>
        <a
          href="https://github.com/nuxt/nuxt.js"
          target="_blank"
          class="button--grey"
        >
          GitHub
        </a>
        {{ response }}
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import Logo from '~/components/Logo.vue'

export default Vue.extend({
  components: {
    Logo
  },
  data() {
    return {
      response: '',
      envVar: process.env.MY_SECRET_VAR
    }
  },
  mounted() {
    this.$axios.$get('/').then((data) => {
      this.response = data
    })
  }
})
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
