<template>
    <h2>Child Component</h2>
    {{mydata}}
    <br><br>
    {{user}}
    <br><br><br>
    <button v-on:click="func()">Click</button>  
</template>

<script>
export default {
  name: 'Child',
 
   props: {
    mydata: String,
    user:Object,
    func:Function
   }
  }
</script>
