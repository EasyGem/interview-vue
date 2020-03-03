<template>
  <div class="sidebar">
    <img src="logo.jpg" alt="" class="sidebar__logo" />

    <div class="sidebar__nav">
      <nuxt-link to="/surveys/add" class="sidebar__nav-item">Опросы</nuxt-link>
      <nuxt-link to="/users" class="sidebar__nav-item">Пользователи</nuxt-link>
      <nuxt-link to="/black-lists" class="sidebar__nav-item">Черные списки</nuxt-link>
      <nuxt-link to="/call-center" class="sidebar__nav-item">Колл-центр</nuxt-link>
    </div>
  </div>
</template>

<style lang="sass" scoped>
.sidebar
  width: 150px
  padding: 20px 0

  &__logo
    width: 60px
    margin-left: auto
    margin-right: auto
    margin-bottom: 32px
    display: block

  &__nav
    &-item
      width: 100%
      padding: 16px
      border-radius: 12px
      margin: 4px 8px
      height: 80px
      display: flex
      align-items: center
      justify-content: center
      text-align: center
      border: 1px solid #ccc
      &.nuxt-link-exact-active
        background-color: #F9FFF9
</style>
