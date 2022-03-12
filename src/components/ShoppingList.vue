<script>
  export default {
    data(){
      return {
        header : "Shopping List App",
        newItem : "",
        items : [
          "10 bags of rice",
          "fuel",
          "Domino Ice-cream"
        ],
      }
    },
    methods:{
      saveItem(){
        if (this.newItem !== "")  {
          this.items.push(this.newItem)
          this.newItem = ""
        }
      }
    }
  }
</script>

<template>
  <h1>{{ header.toLocaleUpperCase() }}</h1>
  <input type="text" v-model="newItem" placeholder="Add an item" @keyup.enter="saveItem">
  <button class="btn btn-primary" @click="saveItem">Save Item</button>
  <ul>
    <li v-for="item in items">{{ item }}</li>
  </ul>
</template>

<style scoped>
a {
  color: #42b983;
}
</style>
