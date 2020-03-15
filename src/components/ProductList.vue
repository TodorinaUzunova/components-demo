<template>
  <div class="hello">
    <h1>{{title}}</h1>
    <input :value="title" @input="changeTitle" />
    <Product v-for="(p,i1) in products" :key="i1">
       <h1 slot="type" >Type: {{p.type}}</h1>
       <h1 slot="price">Price:{{p.price}}</h1>
      <ul  slot="ingredients">
        <li v-for="(ing, i2) in p.ingredients" :key="i2">{{ing}}</li>
      </ul>
    </Product>
    <!-- <Product
      v-for="(p,i) in products"
      :meal-type="p.type"
      :price="p.price"
      :ingredients="p.ingredients"
      :key="i"
    /> without slot-->
  </div>
</template>

<script>
import Product from "./Product.vue";
export default {
  name: "ProductList",
  props: {
       title: String,
    products: Array,
    validator(arr){
        //check all properties
             return arr.every(p=> typeof p.type==='string' 
             && typeof p.price==='number' 
             && Array.isArray(p.ingredients));
    }
   
  },
  data: function() {
    return {}
  },
  components: {
    Product
  },
  methods: {
    changeTitle(e) {
      const value = e.target.value;
      this.$emit("onChangeTitle", value);
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>