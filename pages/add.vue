<template>
  <div class="add-survey">
    hoo
    <tabs-component :tabs="tabs" v-model="activeTab" />

    <component :is="`${activeTab}-component`" />
  </div>
</template>

<script>
import TabsComponent from '@/components/modules/VTabs'

export default {
  components: {
    TabsComponent,
    ParamsComponent: () => import('@/components/surveys/add/tabs/ParamsComponent'),
    QuestionsComponent: () => import('@/components/surveys/add/tabs/QuestionsComponent'),
    LogicComponent: () => import('@/components/surveys/add/tabs/LogicComponent'),
    ConditionsComponent: () => import('@/components/surveys/add/tabs/ConditionsComponent'),
    RespondentsComponent: () => import('@/components/surveys/add/tabs/RespondentsComponent')
  },
  data: () => ({
    activeTab: 'respondents',
    tabs: [
      {
        text: 'Параметры',
        value: 'params'
      },
      {
        text: 'Вопросы',
        value: 'questions'
      },
      {
        text: 'Логика',
        value: 'logic'
      },
      {
        text: 'Условия',
        value: 'conditions'
      },
      {
        text: 'Респонденты',
        value: 'respondents'
      }
    ]
  })
}
</script>

<style lang="sass" scoped></style>
