<template>
  <div id="app">
    <SearchComponent />
  </div>
</template>

<script>
import SearchComponent from "./components/SearchComponent";

export default {
  name: "App",
  components: {
    SearchComponent
  }
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Roboto:wght@300&display=swap");

html,
body {
  font-family: "Roboto", sans-serif;
}
#app {
  font-family: "Roboto", sans-serif;
}
</style>
