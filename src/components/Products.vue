


<template>
    <div class="products">
        <ProductCard
          class="product"  
          v-for="card in cards" 
          v-bind:key="card.name"

          :name="card.name"
          :description="card.description"
          :link="card.link"
          :price="card.price"
     
        />
    </div>
</template>


<script>

import ProductCard from './ProductCard.vue';
export default {
  name: 'Products',
  components: {
    ProductCard
  },
  props: ["cards"],

}
</script>



<style lang="scss" scoped>

.products {

  width: 1028px;
  padding-top: 11px;
  display: grid;


  grid-auto-flow: row;
  grid-template-columns: repeat(3, 1fr);

  // flex-direction: row;
  // flex-wrap: wrap;




  .product {

    width: 332px;
    height: 423px;

    margin-right: 16px;

    background: #FFFEFB;
    box-shadow: 0px 20px 30px rgba(0, 0, 0, 0.04), 0px 6px 10px rgba(0, 0, 0, 0.02);
    border-radius: 4px;
    margin-bottom: 18px;
   
  }
}

</style>
