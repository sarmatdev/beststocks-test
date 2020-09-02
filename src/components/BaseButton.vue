<template>
  <button class="base-button">
    <slot />
  </button>
</template>

<script>
export default {}
</script>

<style lang="scss">
.base-button {
  outline: none;
  background-color: #fff;
  border: 2px solid #db00ff;
  border-radius: 10px;
  font-family: 'Montserrat', sans-serif;
  font-size: 20px;
  cursor: pointer;
  padding: 15px 20px;
  transition: all 0.1s ease-in;

  &:hover:enabled {
    background-color: #db00ff;
    color: #fff;
    box-shadow: 1px 4px 7px rgba(219, 0, 255, 0.5);
  }

  &:disabled {
    cursor: not-allowed;
    background-color: #ccc;
    border: 2px solid #ccc;
    color: #000;
  }
}
</style>
