<template>
  <div id="app">

    <!-- <LikeHeader>
      <h3>初めまして</h3>
      <template v-slot:number>
        <h2>{{number}}</h2>
      </template>
    </LikeHeader>
    <LikeNumber :total-number="number" @my-click="incrementNumber"></LikeNumber> -->

    <button @click="currentComponent = 'Home'">Home</button>
    <button @click="currentComponent = 'About'">About</button>

    <keep-alive>
      <component :is="currentComponent"></component>
    </keep-alive>

  </div>
</template>

<script>

import LikeHeader from "./components/LikeHeader";
import LikeNumber from "./components/LikeNumber";
import Home from "./components/Home";
import About from "./components/About";

export default {
  name: 'App',
  data() {
    return {
      number: 10,
      currentComponent: "Home"
    }
  },
  components: {
    LikeHeader,
    LikeNumber,
    Home,
    About
  },
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
  color: #2c3e50;
  margin-top: 60px;
}
</style>
