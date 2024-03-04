<template>
<div class="header"><h1>ShopWrong</h1></div>
  <div class="container">
    
    <div class="card" v-for="product in supermarket">
      <h2>{{ product.name }}</h2>
      <h2>{{ product.cost }}</h2>
      <img :src="product.img" alt="">
      <h2>{{ product.category }}</h2>
      <button class="buttons" @click="add(product)">Add to Cart!</button>
    </div>
  </div>
<div class="cart"> 
  <div class="total">
        <h2>Total: {{ calculateTotal().toFixed(2) }}</h2>
      </div>
    <div class="cartItems" v-for="item in cart">
      <h2>{{ item.name }}</h2>
      <h2>{{ item.cost }}</h2>
      <img :src="item.img" alt="">
      <h2>{{ item.category }}</h2>
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
    img: "https://s3.amazonaws.com/grocery-project/product_images/honeycrisp-apple-bag-1346504-8116798.jpg"
  },
  {
    name: "Milk",
    cost: 2.49,
    category: "Dairy",
    img: "https://t3.ftcdn.net/jpg/02/23/71/38/360_F_223713833_IVzWUhbC2t3WdN83GoNCPDjHmefthXoq.jpg"
  },
  {
    name: "Bread",      
    cost: 1.99,
    category: "Bakery",
    img: "https://www.backerhausveit.com/wp-content/uploads/2021/03/17783-1.jpg"
  },
  {
    name: "Ground Beef",
    cost: 4.99,
    category: "Meat",
    img: "https://i.dailymail.co.uk/i/pix/2013/04/10/article-0-05701FDF000005DC-667_634x383.jpg"
  },
  {
    name: "Cereal",
    cost: 3.49,
    category: "Breakfast",
    img: "https://www.kelloggs.com/content/dam/Asia/kelloggs_in/images/articles/benefits-of-cereal.jpg"
  },
  {
    name: "Bananas",
    cost: 0.79,
    category: "Produce",
    img: "https://i5.walmartimages.com/asr/3bbb1151-d69a-43fb-b132-47e0bc066307.1f28c1acf3df725a6a39ba4c8738e025.jpeg?odnHeight=768&odnWidth=768&odnBg=FFFFFF"
  },
  {
    name: "Eggs",
    cost: 2.69,
    category: "Dairy",
    img:"https://www.nascoeducation.com/media/catalog/product/cache/465f3046c8658da626e76b96d8ed42e5/c/1/c14067-main_f1cwsmec2g7arwry.jpg"
  },
  {
    name: "Chicken",
    cost: 7.99,
    category: "Meat",
    img:"https://chefsmandala.com/wp-content/uploads/2018/04/Whole-Raw-Chickens.jpg"
  },
  {
    name: "Broccoli",
    cost: 1.29,
    category: "Produce",
    img:"https://www.melissas.com/cdn/shop/products/image-of-organic-broccoli-organics-28658375491628_600x600.jpg?v=1628076836"
  },
  {
    name: "Yogurt",
    cost: 1.49,
    category: "Dairy",
    img:"https://bjs.scene7.com/is/image/bjs/91215?$bjs-Zoom$"
  },
  {
    name: "Chips",
    cost: 3.49,
    category: "Snacks",
    img:"https://assets.syndigo.cloud/cdn/294c4183-1e9e-4ac1-b992-6c0b0cdab112/fileType_jpg;size_600x600/294c4183-1e9e-4ac1-b992-6c0b0cdab112"
  },
  {
    name: "Soda",
    cost: 1.99,
    category: "Beverages",
    img:"https://scene7.samsclub.com/is/image/samsclub/0007800003326_A"
  },
  {
    name: "Cheese",
    cost: 3.49,
    category: "Dairy",
    img:"https://d3mvlb3hz2g78.cloudfront.net/wp-content/uploads/2017/10/thumb_720_450_Swiss_Cheesedreamstime_xl_20274250.jpg"
  },
  {
    name: "Ice Cream",
    cost: 4.49,
    category: "Frozen Foods",
    img: "https://food.fnr.sndimg.com/content/dam/images/food/fullset/2012/6/1/1/FNM_070112-Milky-Way-Ice-Cream-Recipe_s4x3.jpg.rend.hgtvcom.616.462.suffix/1382541468590.jpeg"
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
function calculateTotal() {
  let total = 0;
  for (const item of cart) {
    total += item.cost * (item.amount + 1);
  }
  return total;
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
  text-align: center;
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
 height: 350px;
overflow: hidden;
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
    overflow: hidden;
}

.cartItems {
  margin: 20%;
  margin-top: 5%;
  flex-wrap: wrap;
  align-items: center;
  background-color: #eaf4f4;
  border-radius: 2%;
}
img{
  height: 80px;
}
h1{
  font-size: xxx-large;
}


</style>

