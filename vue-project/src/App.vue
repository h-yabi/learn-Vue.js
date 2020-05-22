<template>
  <div id="app" class="main">

    <button @click="myAnimation = 'slide'">Slide</button>
    <button @click="myAnimation = 'fade'">Fade</button>

    <button @click="show = !show">切り替え</button>
    <!-- <transition
      name="fade"
      type=""
      enter-class=""
      enter-active-class="animate__animated animate__bounce"
      enter-to-class=""
      leave-class=""
      leave-active-class=""
      leave-to-class=""
      appear
    >
      <p v-if="show">Hello</p>
    </transition> -->
    <transition
      :name="myAnimation"
    >
      <p v-if="show">bye</p>
    </transition>

    <transition name="fade" mode="out-in">
      <p
        v-if="show"
        key="bye"
      >さよなら</p>

      <p
        v-else
        key="hello"
      >こんにちは</p>
    </transition>

    <transition
      name="fade"
      @before-enter="beforeEnter"
      @enter="enter"
      @after-enter="afterEnter"
      @enter-cancelled="enterCancelled"
      @before-leave="beforeLeave"
      @leave="leave"
      @after-leave="afterLeave"
      @leave-cancelled="leaveCancelled"
    >
      <div
        class="circle"
        v-if="show"
      ></div>
    </transition>


  </div>
</template>

<script>

export default {
  data() {
    return {
      show: true,
      myAnimation: 'slide'
    }
  },
  methods: {
    beforeEnter(el) {
      // 現れる前
      el.style.transform = 'scale(0)';
    },
    enter(el, done) {
      // 現れる時
      let scale = 0;
      const interval = setInterval(() => {
        el.style.transform = `scale(${scale})`;
        scale += 0.1;
        if(scale > 1) {
          clearInterval(interval);
          done();
        }
      }, 30);
    },
    // afterEnter(el) {
    //   // 現れた後
    // },
    // enterCancelled(el) {
    //   // 現れるアニメーションがキャンセルされた時
    // },
    // beforeLeave(el) {
    //   // 消える前
    // },
    leave(el, done) {
      // 消える時
      let scale = 1;
      const interval = setInterval(() => {
        el.style.transform = `scale(${scale})`;
        scale -= 0.1;
        if(scale < 0) {
          clearInterval(interval);
          done();
        }
      }, 30);
    },
    // afterLeave(el) {
    //   // 消えた後
    // },
    // leaveCancelled(el) {
    //   // 消えるアニメーションがキャンセルされた時
    // }
  },
}
</script>

<style scoped>
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
