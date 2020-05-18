<template>
  <div>
    <label for="title"></label>
    タイトル
    <input
      id="title"
      type="text"
      v-bind:value="value"
      v-on:input="$emit('input', $event.target.value)"
    >
    <pre>
      {{value}}
    </pre>
  </div>
</template>

<script>
export default {
  props: ["value"]
}
</script>