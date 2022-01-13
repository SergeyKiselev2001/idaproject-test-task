

<template>
    <div class="hello">
        <input v-model="newCard.name" />
        <br/>
        <input v-model="newCard.description" />
        <br/>
        <input v-model="newCard.link" />
        <br/>
        <input v-model="newCard.price" />
        <br/>
        <button @click="addCard">OK</button>
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
        name: "DORA",
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



<style scoped>

</style>
