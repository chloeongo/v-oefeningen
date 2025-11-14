<template>
  <div>
    <h2>{{ foodName }}</h2>
    <p>{{ foodDesc }}</p>
    <img src="../assets/logo.svg" v-show="isFavorite" />
  </div>
</template>

<script>
export default {
  props: {
    foodName: {
      //maak een object van een prop als je iets required wilt maken
      type: String,
      required: true,
    },
    foodDesc: {
      type: String,
      required: false,
      default: 'No desc',
    },
    isFavorite: Boolean,
  },
}
</script>

<style scoped>
img {
  width: 50px;
}
</style>
