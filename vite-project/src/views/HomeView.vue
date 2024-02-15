<!-- <DestCard
  v-for="destination in destinations"
  :key="destination.name"
 -->

<template>
  <div class="container"></div>
</template>

<script>
export default {};
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

function makeCard() {
  DOMSelectors.container.insertAdjacentHTML(
    "beforeend",
    `<div class=card>
    <h2>Food: ${name.value} </h2>
    <h2> Book Author: ${cost.value} </h2>  
    <img src="${category.value}" alt="">
   // <button class="button">REMOVE ME</button></div>`
  );
}
makeCard();

</script>
:root{ }
<style lang="scss" scoped></style>
