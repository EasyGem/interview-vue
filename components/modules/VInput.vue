<template>
  <div class="v-input">
    <div class="v-input__field">
      <input type="text" :placeholder="placeholder" :value="value" @input.self="change" ref="input" @keyup.enter.self="submit" />

      <img
        key="two"
        v-if="icon"
        :src="`/img/icons/${icon}.svg`"
        @click="submit"
        class="v-input__icon"
        :class="{ clickable: clickableIcon }"
      />
    </div>
  </div>
</template>

<script>
export default {
  props: {
    value: {
      type: String,
      default: ''
    },
    placeholder: {
      type: String,
      default: ''
    },
    icon: {
      type: String,
      default: ''
    },
    clickableIcon: {
      type: Boolean,
      default: false
    }
  },
  methods: {
    change(e) {
      let value = this.mask ? e : e.target.value
      this.$emit('input', value)
    },
    submit(e) {
      this.$emit('submit', this.$refs.input.value)
    }
  }
}
</script>
