

<template>
    <div class="productAdding">
        <form>
          <label class="labelName">Наименование товара</label>
          <br/>
          <input class="inputName" v-model="newCard.name" placeholder="Введите наименование товара" />
          <br/>
          <label class="labelDescr">Описание товара</label>
          <br/>
          <textarea class="inputDescr" v-model="newCard.description" placeholder="Введите описание товара" />
          <br/>
          <label class="labelLink">Ссылка на изображение товара</label>
          <br/>
          <input class="inputLink" v-model="newCard.link" placeholder="Введите ссылку" />
          <br/>
          <label class="labelPrice">Цена товара</label>
          <br/>
          <input class="inputPrice" v-model="newCard.price" placeholder="Введите цену" />
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

  @mixin label($margin-bottom: 10px, $margin-top: 0px){
      display: block;
      font-family: 'Source Sans Pro';
      font-size: 10px;
      line-height: 13px;
      letter-spacing: -0.02em;
      margin-bottom: $margin-bottom;
      margin-top: $margin-top;
  }

  @mixin input($height:36px, $margin-bottom:10px, $padding-top:1px, $padding-left:16px){
    display: block;
    width: 284px;
    height: $height;
    outline: none;
    border: none;
    background: #FFFEFB;
    box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1);
    border-radius: 4px;
    padding-left: 15px;
    margin-bottom: $margin-bottom;
    margin-top: 0px;
    font-family: Source Sans Pro;
    font-style: normal;
    font-weight: normal;
    font-size: 12px;
    line-height: 15px;
    padding: $padding-top 10px 3px $padding-left;

    &::placeholder{
      
      color: #B4B4B4;
    }
  
  }
  
  input {
    @include input();

  }

  .labelName {
    @include label(-14px, 4px);
  }

  .labelDescr {
    @include label(-14px, -2px);
  }

  .labelLink {
    @include label(-14px, 0px);
  }

  .labelPrice {
    @include label(-14px, 0px);
  }

  .inputName {
    @include input(36px, 0px);
  }

  .inputDescr {
    @include input(108px, -2px, 10px, 16px);
     resize: none;
  }

  .inputLink {
    @include input(36px, -2px);
  }

  .inputPrice {
    @include input(36px, 6px);
  }

  button {
    width: 284px;
    height: 36px;
    background: #EEEEEE;
    border-radius: 10px;
    outline: none;
    border: none;
    cursor: pointer;

    font-family: Inter;
    font-style: normal;
    font-weight: 600;
    font-size: 12px;
    line-height: 15px;

    text-align: center;
    letter-spacing: -0.02em;

    color: #B4B4B4;


    transition: .3s;

    &:hover {
      color: white;
      background: black;
    }
  
  }
}

</style>
