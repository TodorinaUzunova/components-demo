<template>
  <div class="hello">
      <!-- <input @input="changeType"/> -->
    <h1>Type: {{mealType}}</h1>
    <h1>Price:{{price}}</h1>
     <ul>
        <li v-for="(ing, i) in ingredients" :key="i">{{ing}}</li>
     </ul>
  <!-- <div>{{expireDate}}</div> -->
  </div>
</template>

<script>
export default {
  name: 'Product',
  props:{
      mealType:{type:String,
       required:true},
      price:Number,
      ingredients:{
          type:Array,
          validator:(arr)=>{
              return arr.every(i=> typeof i==="string")&& arr.every((i)=>i[0].toUpperCase(i[0]));
          }
          },
      expireDate:{
          type:Date,
          default: ()=> new Date(),
      }
    },
    methods:{
//   changeType(e){
//      const value=e.target.value;  !!! ne se prawi, props are immutable
//      this.type=value;
//   }
        }
}
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