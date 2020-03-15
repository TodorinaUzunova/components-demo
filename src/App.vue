<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
    <ProductList :products="products" :title="title" @onChangeTitle="title=$event"/>
  <!-- <Counter :counter="counter"/>
  <Counter :counter="counter"/>
  <Counter :counter="counter"/> -->
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
//import Counter from './components/Counter.vue'
import ProductList from './components/ProductList.vue'

export default {
  name: 'App',
  data:function(){
    return {
      counter:0,
      products:[
        {
          type:'Spaghetti', price:11, ingredients:['Pasta', 'Meatballs', 'Sauce']
        },
        {
          type:'Musaka', price:12, ingredients:['Potatoes', 'Mince', 'Onion']
          },
        {
          type:'Cake', price:14, ingredients:['Flouer', 'Oil', 'Sugar']
          },
      ],
      title:'This is my product list!',
    }},
    watch:{
      title(newValue, oldValue){
      console.log([newValue, oldValue])

      }
    },
  components: {
    HelloWorld,
     //Counter,
     ProductList
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
