<template>
  <div class="container">
    <div class="card" v-for="product in supermarket">
      <h3>{{ product.name }}</h3>
      <h3>{{ product.cost }}</h3>
      <h3>{{ product.category }}</h3>
      <button @click="add(product)">Add to Cart!</button>
    </div>
  </div>
  <div class="cart">
    <div class="cartItems" v-for="item in cart">
      <h3>{{ item.name }}</h3>
      <h3>{{ item.cost }}</h3>
      <h3>{{ item.category }}</h3>
      <h3>{{ item.amount }}</h3>
      <button @click="remove(item)">Remove From Cart</button>
    </div>
  </div>
</template>

<script setup>
import { reactive } from "vue";
const cart = reactive([]);
const supermarket = [
  {
    name: "Apples",
    cost: 1.99,
    category: "Produce",
    imgs: [""],
  },
  {
    name: "Milk",
    cost: 2.49,
    category: "Dairy",
  },
  {
    name: "Bread",
    cost: 1.99,
    category: "Bakery",
  },
  {
    name: "Ground Beef",
    cost: 4.99,
    category: "Meat",
  },
  {
    name: "Cereal",
    cost: 3.49,
    category: "Breakfast",
  },
  {
    name: "Bananas",
    cost: 0.79,
    category: "Produce",
  },
  {
    name: "Eggs",
    cost: 2.69,
    category: "Dairy",
  },
  {
    name: "Chicken",
    cost: 7.99,
    category: "Meat",
  },
  {
    name: "Broccoli",
    cost: 1.29,
    category: "Produce",
  },
  {
    name: "Yogurt",
    cost: 1.49,
    category: "Dairy",
  },
  {
    name: "Chips",
    cost: 3.49,
    category: "Snacks",
  },
  {
    name: "Soda",
    cost: 1.99,
    category: "Beverages",
  },
  {
    name: "Cheese",
    cost: 3.49,
    category: "Dairy",
  },
  {
    name: "Ice Cream",
    cost: 4.49,
    category: "Frozen Foods",
  },
];
function add(food) {
  if (!cart.includes(food)) {
    cart.push(food);
    food.amount = 1;
  } else {
    food.amount += 1;
  }
}
function remove(item) {
  const index = cart.indexOf(item);
  cart.splice(index);
}
</script>

<style scoped>
.card {
  width: 22%;
}
.container {
  display: flex;
  flex-wrap: wrap;
}
.cart {
  height: 100%; /* Full-height: remove this if you want "auto" height */
  width: 160px; /* Set the width of the sidebar */
  position: fixed; /* Fixed Sidebar (stay in place on scroll) */
  z-index: 1; /* Stay on top */
  top: 0; /* Stay at the top */
  right: 0;
  overflow-x: hidden; /* Disable horizontal scroll */
  padding-top: 20px;
}
</style>
