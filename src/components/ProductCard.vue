



<template>
  <div class="productCardWrapper">
    <div class="delete" @click="deleting(id)">
      <img src="./../assets/delete.svg" alt="delete">
    </div>
    <div class="productCard">
      <img :src='link' alt="product-img">
        <span class="name">{{name}}</span>
        <br>
        <span class="description">{{description}}</span>
        <br>
        <span class="price">{{price_normalized}}</span>
    </div>
  </div>
</template>


<script>
export default {
  name: 'ProductCard',
  props: {
    id: Number,
    name: String,
    description: String,
    link: String,
    price: String
  },

  computed: {
    price_normalized:function(){
      return this.price
        .replace(/[^+\d]/g, '')
        .split("")
        .reverse()
        .map((el,id)=>{
          if (id%3==0){return el + ' '} return el})
        .reverse()
        .join("") + ' руб.';
    }
  },

  methods: {
    deleting: function(id){
      this.$emit('deleteCard', id);
    }
  }
}
</script>



<style lang="scss" scoped>

.productCardWrapper{

  cursor: pointer !important;
  animation: productAnimation .8s ease;
  position: relative;

  .delete {
    position: absolute;
    visibility: hidden;
    z-index: 20;
    top: -8px;
    right: 8px;
    width: 32px;
    height: 32px;
    background: #FF8484;
    box-shadow: 0px 2px 4px rgba(0, 0, 0, 0.1);
    border-radius: 10px;

    display: flex;
    align-items: center;
    justify-content: center;
    
  }

  &:hover .delete {
      visibility: visible;
  }

}

@keyframes productAnimation{
  0%{
    margin-top: -10px;
    opacity: 0;

  }
  100%{
    margin-top: 0px;
    opacity: 1;

  }
}

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
    background: rgba(0,0,0,0.1);
    margin-bottom: 16px;
    object-fit: cover;
    border-radius: 4px 4px 0px 0px;
    cursor: pointer;
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
