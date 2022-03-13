<script>
  export default {
    data(){
      return {
        state : "default",
        header : "Shopping List App",
        newItem : "",
        items : [
          {
            label: "10 bags of rice",
            purchase: true
          },
          {
            label: "fuel",
            purchase: false
          },
          {
            label: "Domino Ice-cream",
            purchase: false
          }
        ],
      }
    },
    methods:{
      saveItem(){
        if (this.newItem !== "")  {
          let newItemObject = {}
          newItemObject.label = this.newItem
          newItemObject.purchase = false
          this.items.push(newItemObject)
          this.newItem = ""
        }
      },
      changeState(state){
        this.state = state
        this.newItem = ""
      },
    }
  }
</script>

<template>
<div class="header">
  <h1>{{ header.toLocaleUpperCase() }}</h1>
  <button v-if="state === 'default'" class="btn btn-primary" @click="changeState('edit')">Add Item</button>
  <button v-else class="btn btn-cancel" @click="changeState('default')">Cancel</button>
  
</div>
  
  <div v-if="state==='edit'" class="add-item-form">
    <input type="text" v-model="newItem" placeholder="Add an item" @keyup.enter="saveItem">
    <button class="btn btn-primary" @click="saveItem" :disabled="newItem.length === 0">Save Item</button>
  </div>
  <ul>
    <li v-for="item in items">{{ item.label }}</li>
  </ul>
  <p v-if="items.length === 0">You are done, Now you can go home with what you've bought</p>
</template>

<style scoped>
body {
  background: #EFF8FF;
  height: 100vh;
  width: 100vw;
  font-family: system-ui, BlinkMacSystemFont, -apple-system, Segoe UI, Roboto, Oxygen, Ubuntu, Cantarell, Fira Sans, Droid Sans, Helvetica Neue, sans-serif;
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 0;
  padding: 0;
}

#shopping-list {
  background: #FFF;
  padding: 2rem;
  margin: 1rem;
  border-radius: 3px;
  box-shadow: 0 4px 8px 0 rgba(0,0,0,0.12), 0 2px 4px 0 rgba(0,0,0,0.08);
  width: 95%;
  max-width: 900px;
}

h1 {
  color: #3D4852;
}

ul {
  list-style: none;
  padding: 0;
}

a {
  color: #6CB2EB;
  font-size: 1.25rem;
  transition: all .1s ease-in;
  margin-top: .5rem;
  display: block;
}

a:hover {
  color: #3490DC;
}

li, p {
  display: flex;
  align-items: center;
  line-height: 1.75;
  letter-spacing: .5px;
  color: #3D4852;
  font-size: 1.25rem;
  cursor: pointer;
  transition: all .1s ease-in;
}

li:hover {
  color: #22292F;
}

li input {
  margin: 0 .5rem 0;
}

#shopping-list > input, #shopping-list > select {
  width: 100%;
  border-radius: 3px;
  box-shadow: 0 2px 4px 0 rgba(0,0,0,0.10);
  border: 1px solid #F1F5F8;
  color: #606F7B;
  padding: .5rem .75rem;
  box-sizing: border-box;
  font-size: 1rem;
  letter-spacing: .5px;
  margin: .5rem 0
}

.add-item-form, .header {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.add-item-form input {
  width: 70%;
  border-radius: 3px;
  box-shadow: 0 2px 4px 0 rgba(0,0,0,0.10);
  border: 1px solid #F1F5F8;
  color: #606F7B;
  padding: .5rem .75rem;
  box-sizing: border-box;
  font-size: 1rem;
  letter-spacing: .5px;
  margin: .5rem 0;
}

.btn {
  border: none;
  border-radius: 3px;
  margin: auto 0;
  padding: .5rem .75rem;
  flex-shrink: 0;
  cursor: pointer;
  font-size: .9rem;
  letter-spacing: .5px;
  transition: all .1s ease-in;
}

.btn[disabled] {
  background: #8795A1;
}

.btn[disabled]:hover {
  background: #606F7B;
}

.btn-primary {
  background: #6CB2EB;
  color: #fff;
}

.btn-primary:hover {
  background: #3490DC;
}

.btn-cancel {
  background: #EF5753;
  color: #fff;
}

.btn-cancel:hover {
  background: #E3342F;
  color: #fff;
}

.strikeout {
  text-decoration: line-through;
  color: #B8C2CC;
}

.strikeout:hover {
  color: #8795A1;
}

.priority {
  color: #DE751F;
}
</style>
