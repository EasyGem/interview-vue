<template>
  <div class="layout">
    <layout-sidebar />
    <div class="layout__content">
      <layout-header />
      <layout-breadcrumbs />
      <nuxt />
    </div>
  </div>
</template>

<script>
import LayoutSidebar from '@/components/layout/LayoutSidebar'
import LayoutHeader from '@/components/layout/LayoutHeader'
import LayoutBreadcrumbs from '@/components/layout/LayoutBreadcrumbs'

export default {
  components: {
    LayoutSidebar,
    LayoutHeader,
    LayoutBreadcrumbs
  }
}
</script>

<style lang="sass" scoped>
.layout
  display: flex
  &__content
    flex: 1
    padding: 20px 40px
</style>
