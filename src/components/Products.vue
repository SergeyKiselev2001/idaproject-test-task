


<template>
    <div class="products">
        <ProductCard
          v-for="card in cards" 
          v-bind:key="card.id"

          :id="card.id"
          :name="card.name"
          :description="card.description"
          :link="card.link"
          :price="card.price"

          @deleteCard="deleteCard"
    
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

  methods: {
    deleteCard: function(id){
      this.$emit('delete', id);
    }
  }

}
</script>



<style lang="scss" scoped>

.products {

  width: 1030px;
  padding-top: 13px;
  display: grid;

  grid-auto-flow: row;
  grid-template-columns: repeat(3, 1fr);

  // flex-direction: row;
  // flex-wrap: wrap;
}


@media (max-width: 1500px) {
  .products {
    grid-template-columns: repeat(2, 1fr);
    width: 500px
  }
}

@media (max-width: 1260px) {
  .products {
    grid-template-columns: repeat(1, 1fr);
    width: 328px
  }
}

</style>
