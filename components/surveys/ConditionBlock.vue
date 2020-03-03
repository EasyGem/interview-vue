<template>
  <div class="condition-block">
    <div class="condition-block__row">
      <p class="condition-block__subtitle" v-text="`Условие ${index + 1}`" />
      <v-select :options="types" v-model="typeSelectedName" @input="setConditionType" />
    </div>

    <div class="condition-block__list">
      <template v-if="typeSelectedName && typeSelected">
        <div class="condition-block__row" v-for="(item, index) in value.conditionValues" :key="index">
          <p>
            <span class="condition-tag" v-if="index > 0">или</span>
            {{ typeSelected.valueName + ' ' + (index + 1) }}
          </p>

          <v-select
            v-if="typeSelected.valueFormat == 'select'"
            :options="typeSelected.selectValues"
            @input="setConditionValue(index, $event)"
          />

          <v-range v-else-if="typeSelected.valueFormat == 'range'" :value="item || []" @input="setConditionValue(index, $event)" />
        </div>
      </template>
    </div>

    <div class="condition-block__row">
      <div></div>
      <div class="condition-block__actions">
        <button class="btn" v-text="`Добавить ${typeSelected.valueName}`" v-if="typeSelectedName && typeSelected" @click="addType()" />
        <div class="l-spacer"></div>
        <button class="btn btn--danger" @click="$emit('remove', index)">Удалить условие</button>
      </div>
    </div>
  </div>
</template>

<script>
import VSelect from '@/components/modules/VSelect'
import VRange from '@/components/modules/VRange'

export default {
  props: {
    value: {
      type: Object,
      default: () => ({
        id: '',
        conditionType: '',
        conditionValues: []
      })
    },
    types: {
      type: Array,
      default: () => []
    },
    index: {
      type: Number,
      default: 0
    }
  },
  data: () => ({
    typeSelectedName: ''
  }),
  methods: {
    setConditionType() {
      let newValue = { ...this.value }
      newValue.conditionType = this.typeSelectedName
      newValue.conditionValues = []
      this.updateData(newValue)
    },
    setConditionValue(index, value) {
      let newValue = { ...this.value }
      newValue.conditionValues[index] = value
      this.updateData(newValue)
    },
    addType() {
      let newValue = { ...this.value }
      newValue.conditionValues.push(null)
      this.updateData(newValue)
    },
    updateData(condition) {
      this.$emit('input', condition)
      let { id } = condition

      try {
        // Условная отправка данных на сервер
        this.$axios.put(`/condition/${id}`, condition)
      } catch (e) {
        console.log(e)
      }

      console.log(condition)
    }
  },
  computed: {
    typeSelected() {
      return this.types.find(e => e.value == this.typeSelectedName)
    }
  },
  components: {
    VRange,
    VSelect
  }
}
</script>

<style lang="sass">
.condition
  &-tag
    padding: 12px 16px
    border-radius: 8px
    background-color: #FAF2E4
    margin-right: 8px

  &-block
    padding: 20px 32px
    background-color: #FDFDF5

    &:nth-child(2n)
      background-color: #F9FFF9
    &:nth-child(3n + 1)
      background-color: #F9FAFD

    &__list
      padding-right: 100px

    &__actions
      display: flex
      margin-top: 40px

    &__row
      margin-bottom: 32px
      display: flex
      align-items: center

      &>:first-child
        min-width: 320px
      &>:last-child
        flex: 1

    &__subtitle
      font-weight: 500
</style>
