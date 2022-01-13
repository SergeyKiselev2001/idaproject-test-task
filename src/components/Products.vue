


<template>
    <div class="hello">
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



<style scoped>



</style>
