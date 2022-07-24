<template>
  <div id="app">
    <convert currencyA="EUR" currencyB="BRL" />
    <convert currencyA="BRL" currencyB="EUR" />
  </div>
</template>

<script>
import Convert from "./components/Converter.vue";
export default {
  name: "App",
  components: {
    Convert,
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
