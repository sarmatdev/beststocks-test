<template>
  <input
    type="number"
    @input="$emit('input', $event.target.value)"
    min="1"
    max="99"
    step="1"
    class="fraction-input"
    :class="{ 'fraction-input--error': error }"
    :value="value"
  />
</template>

<script>
export default {
  props: {
    value: [String, Number],
    error: Boolean
  }
}
</script>

<style lang="scss">
.fraction-input {
  width: 45px;
  height: 45px;
  font-size: 40px;
  border: 2px solid #db00ff;
  border-radius: 6px;
  outline: none;
  background-color: #fff;
  text-align: center;
  padding: 5px;

  &--error {
    background-color: red;
    color: #fff;
  }
}
input::-webkit-outer-spin-button,
input::-webkit-inner-spin-button {
  -webkit-appearance: none;
  margin: 0;
}

input[type='number'] {
  -moz-appearance: textfield;
}
</style>
