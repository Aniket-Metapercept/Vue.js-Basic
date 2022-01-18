<template>
    <h1 :class="{green:isTrue}">{{data.name}}</h1>
    <button v-on:click="func2(data.name)" >Click</button>


    <button v-on:click="isTrue=!isTrue">Change Color</button>


</template>

<script>
export default {
  name: 'MyComponent',
 
   props: {
     data:Object,
     func2:Function
 
   },

   data(){
     return {
      isTrue : false
      }
    },

    methods:{
      func3(){
        if(this.isTrue){
          this.isTrue= false
        }else{
          this.isTrue = true
        }
      }
    }

  }
</script>

<style scoped>
  .green{
    color: green;
  }
</style>