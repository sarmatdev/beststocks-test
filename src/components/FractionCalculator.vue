<template>
  <section class="fraction-calculator">
    <h1>Fraction calculator</h1>
    <main class="fraction-calculator__container">
      <FractionUnit
        v-for="(fraction, id) in fractions"
        :key="id"
        :fraction-props="{
          fraction,
          id,
          isUnitLast: isUnitLast(id),
          allowDelete
        }"
        @deleteFraction="deleteFraction(id)"
      />
      <img src="../assets/icons/equal.svg" alt="equal" />
      <p class="fraction-calculator__result">
        {{ fractionResult }}
      </p>
    </main>
    <BaseButton
      @click.native="addNewFraction"
      :disabled="!allowAddingNewFractions"
    >
      Add new element
    </BaseButton>
  </section>
</template>

<script>
import BaseButton from './BaseButton'
import FractionUnit from './FractionUnit'
export default {
  components: { BaseButton, FractionUnit },
  data() {
    return {
      fractions: [
        {
          dividend: 1,
          divisor: 1
        },
        {
          dividend: 1,
          divisor: 1
        }
      ]
    }
  },
  computed: {
    fractionResult() {
      return this.fractions.reduce((result, fraction) => {
        return fraction.dividend / fraction.divisor + result
      }, 0)
    },
    allowDelete() {
      if (this.fractions.length > 2) return true
      return false
    },
    allowAddingNewFractions() {
      if (this.fractions.length >= 5) return false
      return true
    }
  },
  methods: {
    addNewFraction() {
      this.fractions.push({
        dividend: 2,
        divisor: 2
      })
    },
    deleteFraction(id) {
      this.fractions.splice(id, 1)
    },
    isUnitLast(id) {
      if (this.fractions.length - 1 === id) return true
      return false
    }
  }
}
</script>

<style lang="scss">
.fraction-calculator {
  &__container {
    display: flex;
    align-items: center;
  }

  &__result {
    font-size: 40px;
    margin-left: 10px;
  }
}
</style>
