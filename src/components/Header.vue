


<template>
    <div class="header">
        <div class="title">
          <h2>Добавление товара</h2>
        </div>
    </div>
</template>


<script>
export default {
  name: 'Header',
  props: {
    msg: String,
    mda: String,
  }
}
</script>



<style lang="scss" scoped>

.header {
  
  width: 100%;
  height: 70px;

  .title {
    margin-top: 33px;
    letter-spacing: 0.028em;
    margin-left: 31px;
    font-family: 'Source Sans Pro';
    font-size: 18px;
    font-style: normal;
    font-weight: 600;
    text-align: left;
  }

}



</style>
