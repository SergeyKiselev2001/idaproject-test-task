<template>
  <div class="content">
    <Header @select="filtering"></Header>
    <ProductAdding
      class="productAdding" 
      @add="newCard"
    />
    <Products 
      :cards="cardsToShow"
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

      cardsToShow : [], // Список карточек товаров в отсортированном виде

      filteringOption: 'По умолчанию',

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
    if (localStorage.cards) this.cards = JSON.parse(localStorage.cards);
    this.cardsToShow = this.cards;
  },

  updated: function(){
    localStorage.cards = JSON.stringify(this.cards);
    
  },

  methods: {
    newCard: function(obj){

      // id = последний id в списке товаров c увеличенным id на 1, если товаров нет, тогда id=0
      obj.id = ((this.cards[this.cards?.length-1]?.id) + 1) || 0;
      this.cards = [...this.cards, obj];
      this.filtering(this.filteringOption);
    },

    deleteCard: function(id){
      this.cards = [...this.cards.filter(el=>el.id!=id)];
      this.filtering(this.filteringOption);
    },

    filtering: function(option){

      this.filteringOption = option;

      switch (option){
        case "По умолчанию":
          this.cardsToShow = [...this.cards];
          break;

        case "По цене min":
          this.cardsToShow = [...this.cards].sort(function(a, b) {
              return a.price.replace(/[^+\d]/g, '') - b.price.replace(/[^+\d]/g, '');
          });
          break;

        case "По цене max":
          this.cardsToShow = [...this.cards].sort(function(a, b) {
              return a.price.replace(/[^+\d]/g, '') - b.price.replace(/[^+\d]/g, '');
          }).reverse();
          break;

        case "По наименованию":
          this.cardsToShow = [...this.cards].sort(function(a, b) {
              if(a.name.toLowerCase() < b.name.toLowerCase()) { return -1; }
              if(a.name.toLowerCase() > b.name.toLowerCase()) { return 1; }
              return 0;
          });
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
  justify-content: center;

  
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

@media (max-width: 1500px) {
  .content {
    width: 1228px
  }
}


@media (max-width: 1260px) {
  .content {
    width: 800px
  }
}
</style>
