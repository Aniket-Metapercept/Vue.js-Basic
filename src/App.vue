<template>
 <h1>Hello World</h1>
  <HelloWorld msg="Welcome to Your Vue.js App"/>
  <home></home>

</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import Home from './components/Home.vue'
export default {
  name: 'App',
  components: {
    HelloWorld,
    Home,
  }
}
</script>
