<template>
  <div class="sample">
    いいね！ {{totalNumber}}
    <button @click="increment">クリック</button>
  </div>
</template>

<script>
export default {
  name: 'LikeNumber',
  props: {
    totalNumber: Number
  },
  methods: {
    increment() {
      this.$emit("my-click", this.totalNumber + 1);
    }
  },
}
</script>

<style scoped>
.sample {
  border: 1px solid red;
  padding: 5px;
}
</style>