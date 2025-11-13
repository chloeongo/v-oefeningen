<script>
export default {
  data() {
    return {
      isImportant: true,
      typewriterCount: 2,
      Text: 'hey pizza burger',
      showDiv: false,
      manyFoods: [
        { name: 'Pizza', likes: 0 },
        { name: 'Sushi', likes: 0 },
        { name: 'Hamburger', likes: 0 },
      ],
      count: 0,
      inpCount: 0,
      itemName: null,
      itemNumber: null,
      important: false,
      shoppingList: [{ name: 'Tomatoes', number: 5, important: false }],
      methods: {
        addItem() {
          let item = {
            name: this.itemName,
            number: this.itemNumber,
            important: this.itemImportant,
          }
          this.shoppingList.push(item)
          this.itemName = null
          this.itemNumber = null
          this.itemImportant = false
        },
      },
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

  <div v-show="showDiv">
    <h2>you can see this div</h2>
  </div>
  <h2 v-if="showDiv !== true">now u dont</h2>

  <div>
    <div v-for="(food, index) in manyFoods" v-bind:key="index">
      {{ index }}: {{ food.name }} <br />
      <button class="btn" v-on:click="food.likes++">
        {{ food.likes }} people like {{ food.name }}
      </button>
    </div>
  </div>

  <div>
    <h2>Cookie swiper</h2>
    <img
      v-on:mouseenter="count++"
      src="../assets/pngtree-deliciously-homemade-chocolate-chip-cookies-with-a-perfect-crunch-png-image_15989514.png"
    />
    <p>{{ 'Points: ' + count }}</p>
  </div>

  <div>
    <input v-on:input="inpCount++" />
    <p>{{ 'Input event occured: ' + inpCount }}</p>
  </div>

  <div>
    <form v-on:submit.prevent="addItem">
      <p>Add item</p>
      <p>Item name: <input type="text" required v-model="itemName" /></p>
      <p>How many: <input type="number" v-model="itemNumber" /></p>
      <p>
        Important?
        <label>
          <input type="checkbox" v-model="itemImportant" />
          {{ important }}
        </label>
      </p>
      <button type="submit">Add item</button>
    </form>
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

.btn {
  background-color: aquamarine;
  border: none;
  padding: 10px 20px 10px 20px;
  border-radius: 15px;
}

div {
  margin-top: 20px;
  margin-bottom: 20px;
}

img {
  width: 200px;
  height: 200px;
}
</style>
