


<template>
    <div class="header">
        <div class="title">
          <h2>Добавление товара</h2>
        </div>
        <div class="select">
          <select v-model="selected">
              <option>По умолчанию</option>
              <option>По цене min</option>
              <option>По цене max</option>
              <option>По наименованию</option>

          </select>
        </div>
    </div>
</template>


<script>
export default {
  name: 'Header',
  props: {
    msg: String,
  },
  data(){
    return {
      selected: 'По умолчанию'
    }
  },

  watch: {
    selected: function(){
      this.$emit("select", this.selected);
    }
  }
}
</script>



<style lang="scss" scoped>

.header {
  
  width: 100%;
  height: 70px;

  position: relative;



  .title {
    display: inline-block;
    margin-top: 12px;
    letter-spacing: 0.028em;
    margin-left: 31px;
    font-family: 'Source Sans Pro';
    font-size: 18px;
    font-style: normal;
    font-weight: 600;
    text-align: left;
  }

  .select {
    position: absolute;
    top: 31px;
    right: 32px;
    select {
      padding-left: 12px;
      font-family: Source Sans Pro;
      font-style: normal;
      font-weight: normal;
      font-size: 12px;
      line-height: 15px;
      width: 121.49px;
      height: 36px;
      outline: none;
      border: none;
      color: #B4B4B4;
      background: #FFFEFB;
      box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1);
      border-radius: 4px;
    }
  }

}



</style>
