<template>
  <div id="app" class="main">

    <button @click="myAnimation = 'slide'">Slide</button>
    <button @click="myAnimation = 'fade'">Fade</button>

    <button @click="show = !show">切り替え</button>

    <transition
      :name="myAnimation"
    >
      <p v-if="show">bye</p>
    </transition>

    <br>
    <br>


    <button @click="add">追加</button>
    <ul style="width: 200px; margin: auto;">
      <transition-group name="fade" tag="div">
        <li
          style="cursor: pointer;"
          v-for="(number, index) in numbers"
          @click="remove(index)"
          :key="number"
        >{{ number }}</li>
      </transition-group>
    </ul>



  </div>
</template>

<script>

export default {
  data() {
    return {
      show: true,
      myAnimation: 'slide',
      numbers: [0, 1, 2],
      nextnumber: 3,
    }
  },
  methods: {
    randomIndex() {
      return Math.floor(Math.random() * this.numbers.length);
    },
    add() {
      this.numbers.splice(this.randomIndex(), 0, this.nextnumber);
      this.nextnumber += 1;
    },
    remove(index) {
      this.numbers.splice(index, 1);
    }
  },
}
</script>

<style scoped>
.fade-move {
  transition: transform 1s;
}
.fade-enter {
  /* 現れる時の最初の状態 */
  opacity: 0;

}
.fade-enter-active {
  /* 現れる時のトランジションの状態 */
  transition: opacity .5s;

}
.fade-enter-to {
  /* 現れる時の最後の状態 */
  opacity: 1;

}
.fade-leave {
  /* 消える時の最初の状態 */
  opacity: 1;
}
.fade-leave-active {
  /* 消える時のトランジションの状態 */
  transition: opacity .5s;
  position: absolute;
  width: 200px;
}
.fade-leave-to {
  /* 消える時の最後の状態 */
  opacity: 0;
}

.slide-enter-active {
  animation: slide-in 3s;
}
.slide-leave-active {
  animation: slide-in .5s reverse;
}

@keyframes slide-in {
  from {
    transform: translateX(100px);
  }
  to {
    transform: translateX(0);
  }

}

.main {
  width: 70%;
  margin: 5rem auto;
  text-align: center;
}

.circle {
  width: 200px;
  height: 200px;
  border-radius: 50%;
  margin: auto;
  background: deeppink;
}

</style>
