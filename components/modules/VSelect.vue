<template>
  <select class="v-select" :value="value" @change="$emit('input', $event.target.value)">
    <option v-for="(option, index) in options" :value="option.value || option" v-text="option.text || option" :key="index" />
  </select>
</template>

<script>
export default {
  props: {
    value: {
      type: String,
      default: ''
    },
    options: {
      type: Array,
      default: () => []
    }
  }
}
</script>
