<template>
  <div class="header">
    <div class="header__search">
      <v-input v-model="search.value" v-bind="search" />
    </div>
    <div class="l-spacer"></div>
    <div class="header__user">
      <img src="/user.jpg" alt="" class="header__user-avatar" />
      <div class="header__user-name">
        Alexander Gusev
      </div>
      <div class="header__user-position">Frontend Разработчик</div>
    </div>
  </div>
</template>

<script>
import VInput from '@/components/modules/VInput'

export default {
  components: {
    VInput
  },
  data: () => ({
    search: {
      value: '',
      placeholder: 'Поиск',
      icon: 'search',
      clickableIcon: true
    }
  })
}
</script>

<style lang="sass" scoped>
.header
  display: flex
  align-items: center
  &__search
    flex: 700px 0 0
  &__user
    display: grid
    grid-template-columns: auto auto
    grid-gap: 0 12px
    &-avatar
      height: 50px
      width: 50px
      border-radius: 100px
      grid-row: span 3
    &-name
      font-weight: 600
    &-position
      color: #888
      font-size: 14px
</style>
