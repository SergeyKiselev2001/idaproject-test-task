


<template>
    <div class="products">
        <ProductCard
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
  padding-top: 13px;
  display: grid;


  grid-auto-flow: row;
  grid-template-columns: repeat(3, 1fr);

  // flex-direction: row;
  // flex-wrap: wrap;




}

</style>
