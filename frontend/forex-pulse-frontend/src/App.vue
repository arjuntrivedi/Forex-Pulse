<template>
  <div id="app">
    <h1>Forex Pulse</h1>
    <p>{{ message }}</p>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'App',
  data() {
    return {
      message: "Loading..."
    };
  },
  async created() {
    try {
      const response = await axios.get('http://localhost:5000');  // URL of Flask backend
      this.message = response.data.message;
    } catch (error) {
      console.error('Error connecting to backend:', error);
      this.message = "Failed to connect to backend";
    }
  }
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
