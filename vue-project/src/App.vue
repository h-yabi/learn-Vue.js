<template>
  <div id="app">

    <h1>フォーム</h1>

    <EventTitle v-model="eventData.title"></EventTitle>

    <!-- ↑は下記と同じ意味
    <EventTitle
      :value="eventData.title"
      @input="eventData.title = $event"
    ></EventTitle> -->

    <div>
      <label for="maxNumber"></label>
      最大人数
      <input id="maxNumber" type="number" v-model.trim="eventData.maxNumber">
    </div>

    <div>
      <label for="host"></label>
      主催者
      <input id="host" type="text" v-model.trim="eventData.host">
    </div>

    <div>
      <label for="detail"></label>
      イベント内容<br>
      <textarea id="detail" cols="30" rows="10" v-model="eventData.detail"></textarea>
    </div>

    <hr>

    <div>
      <input type="checkbox" id="isPrivate" v-model="eventData.isPrivate">
      <label for="isPrivate">非公開</label>
      <p>参加条件</p>
      <input
        type="checkbox"
        id="10"
        value="10代"
        v-model="eventData.target"
      >
      <label for="10">10代</label>

      <input
        type="checkbox"
        id="20"
        value="20代"
        v-model="eventData.target"
      >
      <label for="20">20代</label>

      <input
        type="checkbox"
        id="30"
        value="30代"
        v-model="eventData.target"
      >
      <label for="30">30代</label>
    </div>

    <hr>

    <div>
      参加費
      <input
        type="radio"
        id="free"
        value="無料"
        v-model="eventData.price"
        >
      <label for="free">無料</label>

      <input
        type="radio"
        id="paid"
        value="有料"
        v-model="eventData.price"
        >
      <label for="paid">有料</label>
    </div>

    <hr>

    <div>
      開催場所
      <select v-model="eventData.location">
        <option
          v-for="location in locations"
          :key="location"
        >{{location}}</option>
      </select>
    </div>

  </div>
</template>

<script>
import EventTitle from './components/EventTitle'

export default {
  name: 'App',
  data() {
    return {
      locations: ["東京", "大阪", "名古屋"],
      eventData: {
        title: "",
        maxNumber: 0,
        host: "",
        detail: "",
        isPrivate: false,
        target: [],
        price: "無料",
        location: "東京"
      }
    }
  },
  components: {
    EventTitle
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
}
</style>
