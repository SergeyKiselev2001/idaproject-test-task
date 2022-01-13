

<template>
    <div class="productAdding">
        <form>
          <label>Наименование товара</label>
          <br/>
          <input v-model="newCard.name" />
          <br/>
          <label>Описание товара</label>
          <br/>
          <input class="description" v-model="newCard.description" />
          <br/>
          <label>Ссылка на изображение товара</label>
          <br/>
          <input v-model="newCard.link" />
          <br/>
          <label>Цена товара</label>
          <br/>
          <input v-model="newCard.price" />
          <br/>
          <button @click.prevent="addCard">Добавить товар</button>
        </form>
  
    </div>
</template>


<script>
export default {
  name: 'ProductAdding',
  props: {name:String, description:String, link:String, price:String},
  
  data(){
    return {
      da: "fds",
      newCard : {
        name: "",
        description: "",
        link: "",
        price: ""
      }
    }
  },

  methods: {
    addCard: function(){
      this.$emit("event", {
        name: this.newCard.name,
        description: this.newCard.description,
        link: this.newCard.link,
        price: this.newCard.price,
      } );
    }
  }
}
</script>



<style lang="scss" scoped>

.productAdding {
  width: 332px;
  height: 440px;
  background: #FFFEFB;
  box-shadow: 0px 20px 30px rgba(0, 0, 0, 0.04), 0px 6px 10px rgba(0, 0, 0, 0.02);
  border-radius: 4px;
  margin-left: 32px;
  margin-top: 13px;

  padding-top: 20px;
  padding-left: 24px;

  margin-right: 16px;
  

  label {
      font-family: 'Source Sans Pro';
      font-size: 10px;
      line-height: 13px;
      letter-spacing: -0.02em;
      
  }

  input {
    width: 284px;
    height: 36px;
    outline: none;
    border: none;
    background: #FFFEFB;
    box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1);
    border-radius: 4px;

    margin-top: 4px;
    padding-left: 15px;
    margin-bottom: 10px;
  }

  .description {
    height: 108px;
  }

  button {
    width: 284px;
    height: 36px;
    background: #EEEEEE;
    border-radius: 10px;
    outline: none;
    border: none;
    cursor: pointer;

    transition: .3s;

    &:hover {
      color: white;
      background: black;
    }
  
  }
}

</style>
