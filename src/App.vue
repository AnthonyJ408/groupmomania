<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" />
    <HelloWorld msg="Welcome to Your Vue.js App" />
    <p>{{ msg }}</p>
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";
import { API } from "aws-amplify";

export default {
  name: "App",
  components: {
    HelloWorld,
  },
  data(){
    return {
      msg=''
    }
  },
  computed: {
    async fetchgroupomania() {
      API.get("myAPI", "/groupomania", {})
        .then((response) => {
          this.msg = response;
          console.log(`Response: ${response}`);
        })
        .catch((error) => {
          console.log(error.response);
        });
      this.name = "";
      this.description = "";
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
