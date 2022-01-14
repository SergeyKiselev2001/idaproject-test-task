<template>
  <div class="content">
    <Header></Header>
    <ProductAdding
      class="productAdding" 
      @event="newCard"
    />
    <Products 
      :cards="cards"
    />
  </div>

</template>

<script>
import Header from './components/Header.vue';
import ProductAdding from './components/ProductAdding.vue';
import Products from './components/Products.vue';

export default {
  name: 'App',
  components: {Header, ProductAdding, Products},

  data(){
    return {

      cards : [
      {
        name: "Наименование товара",
        description: "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
        link: "https://i.ibb.co/N9rvSD5/Rectangle-31.png",
        price: "10 000 руб."
      },
      {
        name: "Наименование товара",
        description: "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
        link: "https://i.ibb.co/N9rvSD5/Rectangle-31.png",
        price: "10 000 руб."
      },
      ],
    }
  },

  methods: {

    newCard: function(obj){
      this.cards = [...this.cards, obj];
    }

  }
}
</script>

<style lang="scss" scoped>



.content {
  display: flex;
  flex-wrap: wrap;
  width: 1440px;
  margin: 0 auto;
  
}


#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;

  
}
</style>
