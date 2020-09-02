<template>
  <transition appear name="slide">
    <div
      class="fraction-unit"
      @mouseover="deleteButton = true"
      @mouseleave="deleteButton = false"
    >
      <FractionDeleteButton
        @click.native="deleteFraction(fractionProps.id)"
        v-show="deleteButton && fractionProps.allowDelete"
      />
      <div class="fraction-unit__inputs">
        <FractionInput
          v-model.number="fractionProps.fraction.dividend"
          :error="$v.fractionProps.fraction.dividend.$invalid"
        />
        <img src="../assets/icons/fraction-divider.svg" alt="divider" />
        <FractionInput
          v-model="fractionProps.fraction.divisor"
          :error="$v.fractionProps.fraction.divisor.$invalid"
        />
      </div>
      <img
        class="fraction-unit__plus-icon"
        v-if="!fractionProps.isUnitLast"
        src="../assets/icons/plus.svg"
        alt="plus"
      />
    </div>
  </transition>
</template>

<script>
import FractionInput from './FractionInput'
import FractionDeleteButton from './FractionDeleteButton'
import { required, maxValue, integer } from 'vuelidate/lib/validators'
export default {
  props: {
    fractionProps: Object
  },
  components: {
    FractionInput,
    FractionDeleteButton
  },
  data() {
    return {
      deleteButton: false
    }
  },
  validations: {
    fractionProps: {
      fraction: {
        dividend: {
          required,
          minLength: maxValue(99),
          integer
        },
        divisor: {
          required,
          minLength: maxValue(99),
          integer
        }
      }
    }
  },
  methods: {
    deleteFraction(id) {
      this.$emit('deleteFraction', id)
    }
  }
}
</script>

<style lang="scss">
.fraction-unit {
  width: 50px;
  height: 130px;

  position: relative;
  padding: 10px;
  display: flex;
  align-items: center;

  margin: 30px;

  &__inputs {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: space-between;

    height: 140px;
  }

  &__plus-icon {
    margin: 20px;
  }
}
</style>
