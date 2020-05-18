<template>
  <div id="app">

    <h1>フォーム</h1>
    <label for="title"></label>
    <input id="title" type="text" v-model="eventData.title">
    {{eventData}}

  </div>
</template>

<script>

// import LikeHeader from "./components/LikeHeader";
// import LikeNumber from "./components/LikeNumber";
// import Home from "./components/Home";
// import About from "./components/About";

export default {
  name: 'App',
  data() {
    return {
      eventData: {
        title: "タイトル"
      }
    }
  },
  // components: {
  //   LikeHeader,
  //   LikeNumber,
  //   Home,
  //   About
  // },
  methods: {
    incrementNumber(value) {
      this.number = value;
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
}
</style>
