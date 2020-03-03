<template>
  <div class="respondents">
    <div class="respondents__subtitle">Добавить опрос</div>

    <condition-block
      v-for="(condition, index) in conditions"
      :key="condition.id"
      v-model="conditions[index]"
      :types="conditionTypes"
      @remove="removeCondition(index)"
      :index="index"
    />

    <div class="respondents__add" @click="pushCondition">
      Нажмите, чтобы добавить новое условие выборки. <br />
      Все условия связываются между собой логическим "И"
    </div>

    <div class="respondents__actions">
      <button class="btn">Протестировать опрос</button>
      <div class="l-spacer"></div>
      <button class="btn">Далее</button>
    </div>
  </div>
</template>

<script>
import ConditionBlock from '@/components/surveys/ConditionBlock'

export default {
  components: {
    ConditionBlock
  },
  data: () => ({
    conditions: [
      {
        id: 123,
        conditionType: '',
        conditionValues: []
      }
    ],
    conditionTypes: [
      {
        value: '',
        text: 'Выберите условие'
      },
      {
        value: 'cardType',
        text: 'Тип карты лояльности',
        valueName: 'Тип',
        valueFormat: 'select',
        selectValues: ['Bronze', 'Silver', 'Gold']
      },
      {
        value: 'age',
        text: 'Возраст респондента',
        valueName: 'Диапазон',
        valueFormat: 'range'
      },
      {
        value: 'cardStatus',
        text: 'Статус карты лояльности',
        valueName: 'Статус',
        valueFormat: 'select',
        selectValues: ['Активна', 'Неактивна']
      }
    ]
  }),
  methods: {
    removeCondition(index) {
      this.conditions.splice(index, 1)
    },
    pushCondition() {
      this.conditions.push({
        id: Math.random()
          .toString(36)
          .substr(2, 9),
        conditionType: '',
        conditionValues: []
      })
    }
  }
}
</script>

<style lang="sass" scoped>
.respondents
  width: 100%
  box-shadow: 0 0 10px rgba(0,0,0,0.2);
  padding-bottom: 40px
  &__subtitle
    padding: 20px 32px
    font-weight: 500
    color: #ccc
  &__add
    width: auto
    padding: 40px 20px
    margin: 20px
    text-align: center
    border: 2px dashed #97C475
    cursor: pointer
    color: #97C475
    transition: .5s ease
    &:hover
      transform: scale(.95)
    &:active
      transform: scale(1)
  &__actions
    display: flex
    align-items: center
    padding: 20px
</style>
