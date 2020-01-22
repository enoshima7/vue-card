<template>
  <div :class="'product ' + product.color">
    <div class="text">{{product.bgtext}}</div>
    <div class="image">
      <img :src="product.src" alt />
    </div>

    <div class="detail">
      <h2 class="title">{{product.title}}</h2>
      <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Hic in adipisci nihil qui maiores. Repudiandae voluptatibus quod deserunt nulla et. Et tenetur dolore debitis est quasi, molestias hic vitae consequuntur?</p>
    </div>
  </div>
</template>

<script>
export default {
  props: ["product"]
};
</script>

<style>
.product {
  flex: 1 1 33.333%;
  width: 100%;
  padding: 25px;
  position: relative;
  box-shadow: 0px 0px 16px rgba(0, 0, 0, 0.25);
  perspective: 1000px;
  margin-right: 50px;
}
.product.green {
  background-image: linear-gradient(to bottom right, #24d484, #116432);
}
.product.blue {
  background-image: linear-gradient(to bottom left, #24d484, #2474c4 70%);
}
.product.pink {
  background-image: linear-gradient(to bottom right, #f444a4, #1168d4);
}
.text {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  z-index: 0;
  overflow: hidden;
  perspective: 1000px;
  color: #313131;
  font-size: 128px;
  font-weight: 900;
  opacity: 0.2;
  transform-origin: center;
}
.image {
  position: relative;
  z-index: 1;
  transform-origin: center;
}
.image img {
  width: 100%;
  filter: drop-shadow(0px 0px 12px rgba(0, 0, 0, 0.25));
}
.detail {
  background-color: #fff;
  padding: 25px;
  margin: 0px -25px -25px;
}
.detail h2 {
  font-size: 24px;
  font-weight: 700;
  color: #676767;
  margin-bottom: 15px;
}
.detail p {
  font-size: 14px;
  line-height: 1.5;
  font-weight: 300;
  color: #676767;
}
</style>