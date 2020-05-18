<template>
  <div>
    <slot></slot>
  </div>
</template>

<script>
export default {
  name: 'LiekHeader',
  data() {
    return {
      user: {
        firstName: 'Taro',
        lastName: 'Tanaka'
      }
    }
  },
}
</script>