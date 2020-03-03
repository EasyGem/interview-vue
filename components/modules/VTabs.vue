<template>
  <div class="v-tabs">
    <div
      class="v-tabs__item"
      v-for="(tab, index) in tabs"
      :key="index"
      v-text="tab.text"
      @click="$emit('input', tab.value)"
      :class="{ active: value == tab.value }"
    />
  </div>
</template>

<script>
export default {
  props: {
    value: {
      type: String,
      default: ''
    },
    tabs: {
      type: Array,
      default: () => []
    }
  }
}
</script>

<style lang="sass" scoped>
.v-tabs
  display: flex
  align-items: center
  border-bottom: 2px $primary solid
  &__item
    padding: 12px 32px
    cursor: pointer
    transition: opacity .25s ease
    &:hover
      opacity: .75
    &.active
      font-weight: 600
      padding-bottom: 10px
      border-bottom: 2px solid $primary
</style>
