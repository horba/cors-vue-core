<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld :msg="`Ping from server: ${pingResult}`"/>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    HelloWorld
  },
  data() {
    return {
      pingResult: ""
    };
  },
  methods: {
    pingServer() {
      fetch("https://localhost:5001/ping")
        .then(response => response.json())
        .then(response => {
          this.pingResult = response.result;
        });
    }
  },
  created() {
    this.pingServer();
  }
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
