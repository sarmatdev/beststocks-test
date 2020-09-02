<template>
  <transition name="slide">
    <button class="fraction-unit__delete">
      <img src="../assets/icons/delete-cross.svg" alt="" />
    </button>
  </transition>
</template>

<script>
export default {}
</script>

<style lang="scss">
.fraction-unit__delete {
  position: absolute;
  top: -5px;
  right: -14px;
  width: 20px;
  height: 20px;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 50%;
  outline: none;
  border: none;
  background-color: #db00ff;
  cursor: pointer;
}
</style>
