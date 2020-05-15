<template>
  <div id="app">
    <br />
    <br />
    <Form @formato="generate" v-if="!showCard" />
    <Home :file="file" :name="name" :phone="phone" v-if="showCard" />
  </div>
</template>

<script>
import Home from "./views/home";
import Form from "./views/form";
export default {
  name: "App",
  data() {
    return {
      showCard: false,
      name: "",
      file: "",
      phone: ""
    };
  },
  methods: {
    generate(data) {
      this.name = data.name;
      this.file = data.file;
      this.phone = data.phone;
      this.showCard = true;
    }
  },
  components: {
    Home,
    Form
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
