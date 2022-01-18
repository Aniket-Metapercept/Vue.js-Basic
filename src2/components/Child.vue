<template>
    <h2>Child Component</h2>
    {{mydata}}
    <br><br>
    {{user}}
    <br><br><br>
    <button v-on:click="func()">Click</button>  
    <button v-on:click="func4(username)">pass Data to parent</button>  
</template>

<script>
export default {
  name: 'Child',
 
   props: {
    mydata: String,
    user:Object,
    func:Function,
    func4:Function
   },

   data(){
     return {
       username:"aniket Chavan"
     }
   }
  }
</script>
