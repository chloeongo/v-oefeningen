<script></script>

<template>
  <div>
    <h3>Slot component</h3>
    <div>
      <slot name="aSlot"></slot>
    </div>
    <div>
      <slot name="bSlot"></slot>
    </div>
  </div>
</template>

<style scoped>
div {
  background-color: cadetblue;
  padding: 20px;
  color: aliceblue;
}
</style>
