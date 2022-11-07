<template>
  <div id="app">
    <button @click="goRoute">Genesis</button>
  </div>
</template>

<script>

export default {
  name: 'App',
  methods: {
    async goRoute() {
      window.location.href = 'http://localhost:4000/historico-faturas?token=123456';
    },
  },
};
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
