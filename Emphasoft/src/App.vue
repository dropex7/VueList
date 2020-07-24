<template>
  <div id="app">
    <Header />
    <Content />
  </div>
</template>

<script>
import Header from "./components/Header";
import Content from "./components/Content";
export default {
  name: "App",
  components: { Header, Content },
};
</script>

<style>
body {
  margin: 0;
  padding: 0;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #f8f8f8;
  background-color: #282a36;
  display: flex;
  min-height: 100vh;
  flex-direction: column;
}
</style>
