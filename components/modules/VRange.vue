<template>
  <div class="v-range">
    от
    <div class="v-input">
      <div class="v-input__field">
        <input type="text" :value="value[0]" @input="change($event.target.value, 0)" ref="input" />
      </div>
    </div>
    до
    <div class="v-input">
      <div class="v-input__field">
        <input type="text" :value="value[1]" @input="change($event.target.value, 1)" ref="input" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    value: {
      type: Array,
      default: () => ['', '']
    }
  },
  methods: {
    change(val, index) {
      let newVal = [...this.value]
      newVal[index] = val
      this.$emit('input', newVal)
    }
  }
}
</script>
