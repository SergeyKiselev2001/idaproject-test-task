<template>
  <div class="content">
    <Header @select="filtering"></Header>
    <ProductAdding
      class="productAdding" 
      @add="newCard"
    />
    <Products 
      :cards="cards"
      @delete="deleteCard"
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
        price: "10 000 руб.",
        id: 0,
      },
      {
        name: "Наименование товара",
        description: "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
        link: "https://i.ibb.co/N9rvSD5/Rectangle-31.png",
        price: "1000 рублей",
        id: 1,
      },
      {
        name: "Наименование товара",
        description: "Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк",
        link: "https://i.ibb.co/N9rvSD5/Rectangle-31.png",
        price: "2000",
        id: 2,
      },
      ],
    }
  },


  mounted: function(){
    //this.cards = JSON.parse(localStorage.cards);
  },

  updated: function(){
    localStorage.cards = JSON.stringify(this.cards);
  },

  methods: {
    newCard: function(obj){

      // id = последний id в списке товаров c увеличенным id на 1, если товаров нет, тогда id=0
      obj.id = ((this.cards[this.cards?.length-1]?.id) + 1) || 0;
      this.cards = [...this.cards, obj];
    },

    deleteCard: function(id){
      this.cards = [...this.cards.filter(el=>el.id!=id)];
    },

    filtering: function(option){
      switch (option){
        case "По умолчанию":
          
          break;
        case "По цене min":
          this.cards = this.cards.sort(function(a, b) {
              return a.price.replace(/[^+\d]/g, '') - b.price.replace(/[^+\d]/g, '');
          });
          break;
        case "По цене max":
          this.cards = this.cards.sort(function(a, b) {
              return a.price.replace(/[^+\d]/g, '') - b.price.replace(/[^+\d]/g, '');
          }).reverse();
          break;
      }
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
