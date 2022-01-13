<template>
  <div class="content">
    <Header class="header"></Header>
    <ProductAdding
      class="productAdding" 
      name="name"
      description="description"
      link="link"
      price="price"

      @event="newCard"
    />
    <Products 
      class="products"
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
      smth: "LOOOOOOOOOOOOOOOL",

      cards : [{
        name: "Моё имя",
        description: "Описание товара 1",
        link: "1",
        price: "1250"
      },
      {
        name: "Моё имя 2",
        description: "1",
        link: "1",
        price: "500"
      }],
    }
  },

  methods: {

    newCard: function(obj){
      this.cards = [...this.cards, obj];
    }

  }
}
</script>

<style>


.content {
  display: flex;
  flex-wrap: wrap;
  width: 100%;
  
}

.header {
  width: 100%;
  border: 1px solid red;
  height: 100px;
  box-sizing: border-box;
}

.productAdding{
  width: 30%;
  border: 1px solid red;
  box-sizing: border-box;

  height: 500px;
}


.products {
  width: 70%;
  border: 1px solid red;
  box-sizing: border-box;
  height: 500px;
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
