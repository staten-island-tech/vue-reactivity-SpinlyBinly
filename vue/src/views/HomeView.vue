<template>
<div class="header"></div>
  <div class="container">
    
    <div class="card" v-for="product in supermarket">
      <h3>{{ product.name }}</h3>
      <h3>{{ product.cost }}</h3>
      <h3>{{ product.category }}</h3>
      <button class="buttons" @click="add(product)">Add to Cart!</button>
    </div>
  </div>
<div class="cart">
    <div class="cartItems" v-for="item in cart">
      <h3>{{ item.name }}</h3>
      <h3>{{ item.cost }}</h3>
      <h3>{{ item.category }}</h3>
      <button class="buttons" @click="remove(item)">Remove From Cart</button>
    </div>
    </div>
</template>  

<script setup> ;
import { reactive } from "vue";
const cart = reactive([]);
const supermarket = [
  {
    name: "Apples",
    cost: 1.99,   
    category: "Produce",
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
    food.amount = 0;
  } else {
    const index = cart.indexOf(food);
    cart[index].amount+=1;  }
}
function remove(item) {
  const index = cart.indexOf(item);
  cart.splice(index, 1);
}
</script>

<style scoped>
.buttons{
border: 0;
}

.header{
  width: 69.5%;
  height: 10vh;
  background-color: #6b9080;
}
body { 
    background-color: #eaf4f4;
    font-family: Interstate, sans-serif;
    font: 200;
    font-size: x-large;
}
.card {
  width: 15%;
  background-color: #cce3de;
  border-radius: 3%;
  margin: 1%;
 text-align: center;

}
.container {
  display: flex;
  flex-wrap: wrap;
  width: 82%;
}
.cart {
  height: 100%; 
  width: 30%; 
  position: fixed; 
  z-index: 1;
  top: 0;
  right: 0;
  overflow-x: hidden; 
  padding-top: 20px;
    background-color: #a4c3b2;
    text-align: center;
}

.cartItems {
  margin: 20%;
  margin-top: 5%;
  flex-wrap: wrap;
  align-items: center;
  background-color: #eaf4f4;
  border-radius: 2%;
}
</style>

