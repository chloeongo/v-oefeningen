<script>
export default {
  data() {
    return {
      isImportant: true,
    }
  },
}
</script>

<template>
  <div>
    <!-- v afkorting v-bind : -->
    <div :class="{ myClass: isImportant }">Text example</div>
  </div>
</template>

<style>
.myClass {
  background-color: rgb(226, 43, 128);
  padding: 20px;
  border-radius: 20px;
  border: 1px solid #fff;
  color: #fff;
}
</style>
