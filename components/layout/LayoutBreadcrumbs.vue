<template>
  <div class="breadcrumbs">
    <nuxt-link to="/" class="breadcrumbs__item">
      Главная
    </nuxt-link>

    <span class="breadcrumbs__divider">–</span>

    <nuxt-link to="/surveys" class="breadcrumbs__item">
      Опросы
    </nuxt-link>

    <span class="breadcrumbs__divider">–</span>

    <nuxt-link to="/surveys/add" class="breadcrumbs__item">
      Добавить опрос
    </nuxt-link>
  </div>
</template>

<script>
export default {}
</script>

<style lang="sass" scoped>
.breadcrumbs
  display: flex
  align-items: center
  font-size: 14px
  padding: 32px 0
  &__divider
    margin: 0 6px
  &__item
    color: #888
    &.nuxt-link-exact-active
      color: $text-primary
</style>
