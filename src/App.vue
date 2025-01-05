<template>
  <input type="text" v-model="name">
  <button @click="say_hello">say hello</button>
  <p>{{ greeting }}</p>
</template>

<script>
export default {
  data() {
    return {
      greeting: '',
      name: ''
    }
  },
  name: 'App',
  components: {
  },
  methods: {
    async say_hello() {
      const response = await window.__TAURI__.core.invoke('greet', { name: this.name });
      this.greeting = response;
    }
  },

  }
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
