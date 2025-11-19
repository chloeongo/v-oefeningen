<script setup>
import { RouterLink, RouterView } from 'vue-router'
import ToDoItem from './components/ToDoItem.vue'
import FoodItem from './components/FoodItem.vue'
import SlotComp from './components/SlotComp.vue'
import Comp from './components/Comp.vue'
</script>

<template>
  <header>
    <div class="wrapper">
      <nav>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/about">About</RouterLink>
      </nav>
    </div>
  </header>

  <div id="app">
    <h1>testing</h1>
    <ul>
      <li>
        <ToDoItem />
        <food-item food-name="Sushi" food-desc="Japans eten" @toggle-favorite="receiveEmit" />
        <food-item food-name="Banana" food-desc="geel fruit" @toggle-favorite="receiveEmit" />
        <food-item food-name="Rice" @toggle-favorite="receiveEmit" />
      </li>
    </ul>

    <div>
      <SlotComp #aSlot>
        <h5>We buns</h5>
        <p>dit zit boven</p>
      </SlotComp>
      <SlotComp v-slot:bSlot>
        <h5>W</h5>
        <p>deze onder</p>
      </SlotComp>
    </div>
    <Comp />
  </div>

  <RouterView />
</template>

<style scoped>
header {
  line-height: 1.5;
  max-height: 100vh;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

nav {
  width: 100%;
  font-size: 12px;
  text-align: center;
  margin-top: 2rem;
}

nav a.router-link-exact-active {
  color: var(--color-text);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  nav {
    text-align: left;
    margin-left: -1rem;
    font-size: 1rem;

    padding: 1rem 0;
    margin-top: 1rem;
  }
}
</style>
