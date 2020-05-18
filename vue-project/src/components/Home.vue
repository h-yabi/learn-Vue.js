<template>
  <div>
    <p v-border:solid.round.shadow="{width: '10px', color: 'red'}">Home</p>
    <h2>{{ title | upperCase }}</h2>
    <h2>{{ title | lowerCase | upperCase }}</h2>
  </div>
</template>

<script>
export default {
  data() {
    return {
      title: 'Welcome to Tokyo'
    }
  },
  filters: {
    lowerCase(value) {
      return value.toLowerCase();
    }
  },
  directives: {
    border(el, binding) {
      el.style.borderWidth = binding.value.width;
      el.style.borderColor = binding.value.color;
      el.style.borderStyle = binding.arg;
      if (binding.modifiers.round) {
        el.style.borderRadius = "20px";
      }
      if (binding.modifiers.shadow) {
        el.style.boxShadow = "0 2px 5px rgba(0, 0, 0, .35)";
      }
    }
  }
}
</script>