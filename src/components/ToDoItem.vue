<script>
export default {
  data() {
    return {
      isImportant: true,
      typewriterCount: 2,
      Text: 'hey pizza burger',
    }
  },
}
</script>

<template>
  <div>
    <!-- v afkorting v-bind : -->
    <div :class="{ myClass: isImportant }">Text example</div>

    <div class="if">
      <p v-if="typewriterCount > 3">In stock</p>
      <p v-else-if="typewriterCount > 0">Very few left!</p>
      <p v-else>Not in stock</p>

      <div v-if="Text.includes('pizza')">
        <p>The text includes pizza</p>
      </div>
      <p v-else>The word pizza not included</p>
      <div v-if="Text.includes('burger')">
        <p>The text includes burger</p>
      </div>
      <p v-else>The word burger not included</p>
    </div>
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
