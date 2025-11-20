<script>
export default {
  data() {
    return {
      inpAddress: '',
      feedbackText: '',
      myClass: 'invalid',
      rangeVal: 70,
      taskName: null,
      taskDesc: null,
      taskList: [{ name: '', desc: '' }],
      msgAndId: '',
      birbCount: 0,
      isImportant: true,
      typewriterCount: 2,
      Text: 'hey pizza burger',
      text: '',
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
    }
  },
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
    changeText() {
      this.text = 'Hello World!'
    },
    addBirb(number) {
      this.birbCount += number
    },
    myMethod(e, msg) {
      this.msgAndId = msg + ', '
      this.msgAndId += e.target.id
    },
    addTask() {
      let task = {
        name: this.taskName,
        desc: this.taskDesc,
      }
      this.taskList.push(task)
      this.taskName = null
      this.taskDesc = null
    },
  },
  watch: {
    rangeVal(val) {
      if (val > 20 && val < 60) {
        if (val < 40) {
          this.rangeVal = 20
        } else {
          this.rangeVal = 60
        }
      }
    },
    npAddress(newVal, oldVal) {
      if (!newVal.includes('@')) {
        this.feedbackText = 'The e-mail address is NOT valid'
        this.myClass = 'invalid'
      } else if (!oldVal.includes('@') && newVal.includes('@')) {
        this.feedbackText = 'Perfect! You fixed it!'
        this.myClass = 'valid'
      } else {
        this.feedbackText = 'The e-mail address is valid :)'
      }
    },
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

  <div>
    <p>Click on the box below:</p>
    <div v-on:click="changeText" class="methodBox">
      {{ text }}
    </div>

    <div>
      <h2>Birb counter</h2>
      <p>{{ birbCount }}</p>
      <button class="btn" @click="addBirb(1)">+1</button>
      <button class="btn" @click="addBirb(5)">+5</button>
      <button class="btn" @click="addBirb(-1)">-1</button>

      <div>
        <img src="../assets/logo.svg" id="tiger" v-on:click="myMethod($event, 'Hello')" />
        <p>"{{ msgAndId }}"</p>
      </div>
    </div>

    <div class="formDiv">
      <h1>Add task</h1>
      <form @submit.prevent="addTask">
        <label for="task">Task</label> <br />
        <input name="task" type="text" required v-model="taskName" /> <br />

        <label for="taskDesc">Description</label> <br />
        <input name="taskDesc" type="text" required v-model="taskDesc" /> <br />

        <button class="btn" style="margin-top: 10px">Enter</button>
      </form>
      <ul>
        <li v-for="task in taskList">{{ task.name }}, {{ task.desc }}</li>
      </ul>
    </div>
  </div>

  <div>
    <input type="range" v-model="rangeVal" />
    <p>{{ rangeVal }}</p>

    <br />

    <input v-type="email" v-model="inpAddress" />
    <p v-bind:class="myClass">{{ feedbackText }}</p>
  </div>
</template>

<style>
.formDiv {
  padding: 20px;
  border-radius: 20px;
  background-color: rgb(255, 0, 144);
  color: #fff;
}

.formDiv input {
  padding: 0.6em;
  border-radius: 10px;
  border: none;
}

.myClass {
  background-color: rgb(226, 43, 128);
  padding: 20px;
  border-radius: 20px;
  border: 1px solid #fff;
  color: #fff;
}

.methodBox {
  background-color: lightgreen;
  padding: 20px;
  font-weight: bold;
  font-family: 'Courier New', Courier, monospace;
}

.btn {
  background-color: aquamarine;
  border: none;
  padding: 10px 20px 10px 20px;
  border-radius: 15px;
  margin-right: 10px;
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
