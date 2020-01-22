<template>
  <div id="app" @mousemove="mousemove">
    <div class="products-wrraper">
      <Product v-for="product in products" :key="product.color" :product="product" />
    </div>
  </div>
</template>

<script>
import Product from "./components/Product";
export default {
  name: "app",
  components: {
    Product
  },
  data() {
    return {
      products: [
        {
          title: "Nike Air Max",
          color: "green",
          bgtext: "NIKE",
          src: require("./assets/green-shoe.png")
        },
        {
          title: "Nike flex",
          color: "blue",
          bgtext: "AIR",
          src: require("./assets/blue-shoe.png")
        },
        {
          title: "Nike Roche Runs",
          color: "pink",
          bgtext: "MAX",
          src: require("./assets/pink-shoe.png")
        }
      ]
    };
  },
  methods: {
    mousemove(e) {
      let mouseX = e.clientX;
      let mouseY = e.clientY;
      //拿到每个product组件元素
      let products = document.querySelectorAll('.products-wrraper .product');

      for (let i = 0; i < products.length; i++) {
        let product = products[i];
        //拿到图片元素
        let product_image = product.querySelector('.image');
        let img_x = mouseX - this.coords(product_image).x;
        let img_y = mouseY - this.coords(product_image).y;
        //改变位移
        product_image.style.transform = `translateY(-${img_y/40}px) translateX(-${img_x/40}px) translateZ(100px)`;
        //拿到背景文字元素
        let bgtext = product.querySelector('.text');
        let bg_x = mouseX - this.coords(bgtext).x
        let bg_y = mouseY - this.coords(bgtext).y
        //改变位移
        bgtext.style.transform = `translateX(${bg_x/25}px) translateY(${bg_y/25}px)`
      }
    },
    coords(el) {
      //拿到元素离窗口左边和上边的像素
      let coords = el.getBoundingClientRect();
      return {
        x: coords.left / 2,
        y: coords.top / 2
      };
  }
}
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
body {
  font-family: "montseratt", sans-serif;
}
#app {
  width: 100vw;
  min-height: 100vh;
  background-color: #eee;
  display: flex;
  justify-content: center;
  align-items: center;
  overflow: hidden;
}
.products-wrraper {
  display: flex;
  max-width: 1280px;
  padding: 25px;
  margin: 0 auto;
}
</style>
