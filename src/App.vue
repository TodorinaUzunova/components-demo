<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <button @click="selectedComponent='HelloWorld'">Render Hello World</button>
    <button @click="selectedComponent='ProductList'">Render ProductList</button>
    <keep-alive>
    <component :is="selectedComponent"  msg="Welcome to Your Vue.js App"
    :products="products"
    :title="title"
    @onChangeTitle="title=$event">
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/>
    <ProductList :products="products" :title="title" @onChangeTitle="title=$event"/> -->
    </component>
    </keep-alive>
    <button  @click="selectedComponent='Register1'"></button>
    <button @click="selectedComponent='Register'"></button>  
  <!-- <Counter :counter="counter"/>
  <Counter :counter="counter"/>
  <Counter :counter="counter"/> -->
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue';
//import Counter from './components/Counter.vue';
import ProductList from './components/ProductList.vue';
import Register1 from './components/Register1.vue';
import Register from './components/Register.vue';

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
      selectedComponent:'HelloWorld',
    }},
    watch:{
      title(newValue, oldValue){
      console.log([newValue, oldValue])

      }
    },
  components: {
    HelloWorld,
     //Counter,
     ProductList,
     Register1,
     Register
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
