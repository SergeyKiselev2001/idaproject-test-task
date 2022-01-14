

<template>
    <div class="productAdding">
        <form>

          <label class="labelName">Наименование товара</label>
          <br/>
          <div class="inputContainer">
            <div :class="{inputWrapper:nameTouched && !name}">
              <input 
                  @blur="this.nameTouched=true" 
                  class="inputName"

                  v-bind:class="{red_input: nameTouched && !name}"

                  spellcheck="false"
                  v-model="name" 
                  placeholder="Введите наименование товара" />
            </div>
          </div>
          <br/>

          <label class="labelDescr">Описание товара</label>
          <br/>
          <textarea class="inputDescr" spellcheck="false" v-model="description" placeholder="Введите описание товара" />
          <br/>

          <label class="labelLink">Ссылка на изображение товара</label>
          <br/>
          <div class="inputContainer">
            <div :class="{inputWrapper:linkTouched && !link}">
              <input 
                  @blur="linkTouched=true" 
                  class="inputLink" 
                  v-bind:class="{red_input: linkTouched && !link}"
                  spellcheck="false"
                  v-model="link" 
                  placeholder="Введите ссылку" />
            </div>
          </div>
          <br/>

          <label class="labelPrice">Цена товара</label>
          <br/>
          <div class="inputContainer">
            <div :class="{inputWrapper:priceTouched && !price}">
              <input 
                  @blur="priceTouched=true" 
                  class="inputPrice"
                  v-bind:class="{red_input: priceTouched && !price}"
                  spellcheck="false" 
                  v-model="price" 
                  placeholder="Введите цену" />
            </div>
          </div>
          <br/>

          <button v-if="isGreen" class="button_green" @click.prevent="addCard">Добавить товар</button>
          <button v-else disabled>Добавить товар</button>
          
        </form>
  
    </div>
</template>


<script>
export default {
  name: 'ProductAdding',

  
  data(){
    return {
      name: "",
      description: "",
      link: "",
      price: "",

      nameTouched: false,
      linkTouched: false,
      priceTouched: false,
      
      isGreen: false,
    }
  },

  watch: {
    name: function(){
      (this.name && this.link && this.price) ? this.isGreen = true : this.isGreen = false;
    },
    link: function(){
      (this.name && this.link && this.price) ? this.isGreen = true : this.isGreen = false;
    },
    price: function(){
      (this.name && this.link && this.price) ? this.isGreen = true : this.isGreen = false;
    }
  },

  methods: {
    addCard: function(){
      this.$emit("event", {
        name: this.name,
        description: this.description,
        link: this.link,
        price: this.price,
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
      width: fit-content;
      font-family: 'Source Sans Pro';
      font-size: 10px;
      line-height: 13px;
      letter-spacing: -0.02em;
      margin-bottom: $margin-bottom;
      margin-top: $margin-top;
  }

  @mixin required(){
    position: relative;
    &::after{
        content: '';
        position: absolute;
        width: 4px;
        height: 4px;
        right: -5px;
        top: 0px;

        background: #FF8484;
        border-radius: 4px;
    }
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
    position: relative;

    &::placeholder{
      
      color: #B4B4B4;
    }

    
  
  }
  
  input {
    @include input();

  }

.inputContainer{
  position: relative;
  .inputWrapper {
    &::after {
      content: "Поле является обязательным";
      position: absolute;
      color: red;
      width: 100px;
      height: 10px;
      bottom: -14px;
      left: 0px;
      font-family: Source Sans Pro;
      font-style: normal;
      font-weight: normal;
      font-size: 8px;
      line-height: 10px;
      letter-spacing: -0.02em;
      color: #FF8484;
    }
  }
}

  

  .red_input {
    border: 1px solid #FF8484 !important;
    
  }

  .labelName {
    @include label(-14px, 4px);
    @include required();
  }

  .labelDescr {
    @include label(-14px, -2px);
  }

  .labelLink {
    @include label(-14px, 0px);
    @include required();
  }

  .labelPrice {
    @include label(-14px, 0px);
    @include required();
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
    padding-bottom: 3px;

    color: #B4B4B4;


    
  
  }

  .button_green{
    background: #7BAE73;
    color: #FFFFFF;
    transition: .3s;

    &:hover {
      color: white;
      background: black;
    }
  }
}

</style>
