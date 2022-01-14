



<template>
    <div class="productCard">
      <img :src='link' alt="product-img">
        <span class="name">{{name}}</span>
        <br>
        <span class="description">{{description}}</span>
        <br>
        <span class="price">{{price}}</span>
    </div>
</template>


<script>
export default {
  name: 'ProductCard',
  props: {
    name: String,
    description: String,
    link: String,
    price: String
  }
}
</script>



<style lang="scss" scoped>


.productCard {
  width: 332px;
  height: 423px;
  margin-right: 16px;
  background: #FFFEFB;
  box-shadow: 0px 20px 30px rgba(0, 0, 0, 0.04), 0px 6px 10px rgba(0, 0, 0, 0.02);
  border-radius: 4px;
  margin-bottom: 17px;
  overflow: hidden;
  position: relative;
  cursor: pointer;
  transition: .4s ease;

  &:hover {
    box-shadow: 0px 2px 8px 3px rgba(0, 0, 0, 0.24);
  }


  span {
    cursor: auto;
  }

  img {
    display: block;
    width: 332px;
    height: 200px;
    background: gray;
    margin-bottom: 16px;
  }

  .name {
    display: block;
    font-family: 'Source Sans Pro';
    font-style: normal;
    font-weight: 600;
    font-size: 20px;
    line-height: 25px;
    color: #3F3F3F;
    margin-left: 16px;
    margin-bottom: -2px;
  }

  .description {
    width: 300px;
    height: 80px;
    overflow: hidden;
    display: block;
      
    font-family: 'Source Sans Pro';
    font-style: normal;
    font-weight: normal;
    font-size: 16px;
    line-height: 20px;
    margin-left: 16px;
    color: #3F3F3F;

    margin-bottom: 15px;

  }

  .price {
    display: block;
    position: absolute;
    font-family: 'Source Sans Pro';
    font-style: normal;
    font-weight: 600;
    font-size: 24px;
    line-height: 30px;
    color: #3F3F3F;
    
    top: 370px;
    left: 16px;
  }
}

</style>
