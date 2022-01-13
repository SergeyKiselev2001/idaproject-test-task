



<template>
    <div class="productCard">
        {{name}}
        <br>
        {{description}}
        <br>
        {{link}}
        <br>
        {{price}}
    </div>
</template>


<script>
export default {
  name: 'ProductCard',
  props: {
    name: String,
    description: String,
    link: String,
    price: String
  }
}
</script>



<style lang="scss" scoped>

.productCard {
  height: 100px;
  width: 300px;
  background-color: gray;
}

</style>
