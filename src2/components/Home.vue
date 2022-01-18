<template>
    <h1>Home Component  {{email}}</h1> 
    <h1>Home Component  {{email}}</h1> 
    <h1>Name {{ getName() }}</h1>   
    <h1>All data  {{ getData() }}</h1>   
    <h1>data Name - {{ getData().name }}</h1>   
    <h1>data Email - {{ getData().email }}</h1>   
    <h1>Old Email - {{ getData().oldemail }}</h1>   

    <button v-on:click="test()">Click Me</button>
    <button v-on:dblclick="test()">Dbl Click Me</button>
    <h3 v-on:mousemove="hover()">Lorem ipsum dolor sit amet consectetur adipisicing elit. Facere nostrum velit id veritatis ex cupiditate commodi laboriosam inventore, eum officia tenetur aliquid minus dolorum, earum aut voluptatem doloremque corporis quos!</h3>

    {{cnt}}


    <input type="text" name="" v-model="mname" id=""/>
    
    {{mname}}

    <br><br><br>
  
<!-- CheckBox and radio button -->
    <input type="text" name="" v-model="em" id="" placeholder="Email"/><br>
    <input type="text" name="" id="" placeholder="Password" v-model="pass"/><br>
    <button v-on:click="onSubmit()">Submit</button>
 
    <br>
    <label for="java">Java</label>
    <input type="checkbox" name="java" id="java" v-model="technology" value="java">
    <label for="python">python</label>
    <input type="checkbox" name="py" id="python" v-model="technology" value="python">
    <label for="js">Js</label>
    <input type="checkbox" name="js" id="js" v-model="technology" value="js">

    <br><br><br>
    Student<input type="radio" name="stu" id=""  value="student" v-model="whoAmI"><br>
    Professer<input type="radio" name="stu" id="" value="professer" v-model="whoAmI">

    <h3>technology-{{technology}}</h3>
    <h2>Who Am I {{whoAmI}}</h2>


    <!-- If else -->
    <div v-if="show"> true if condition</div>
    <div v-else> true else condition</div>


    <!-- for loop -->
    <ol>
        <li v-for="i in lst" :key="i">{{i}}</li>
    </ol>


    <div v-for="i in user" :key="i"> 
        {{i}}
    </div>
    <!-- Child Component -->
    {{childUser}}
    <child mydata="this the Data" :user="user" :func="fun" :func4="fun4"></child>
    
    
    <div v-for="i in user" :key="i">
    
        <MyComponent :data="i" :func2="fun2"></MyComponent>
    </div>

    
    <MyForm></MyForm>
    <br><br><br><br><br>
                <!--  Dynamic Component  -->
    <button @click="tab='Java'">Load Java</button>
    <button @click="tab='node'">Load node</button>
    <button @click="tab='Php'">Load php</button>
<!--     
    <Java/>
    <node/>
    <Php/> -->

    <component :is="tab" />

</template>

<script>
import Child from './Child.vue';
import Java from './Java.vue';
import Php from './Php.vue';
import node from './node.vue';

import MyForm from './MyForm.vue'
import MyComponent from './MyComponent.vue'
export default {
  name: 'Home',
  components:{
      Child,
      MyComponent,
      MyForm,
      Java,
      Php,
      node
      
  },

  props: {
    
  },

  beforeCreate(){
      alert("Before create call")
  },
  created(){
      alert("create call")
  },
  data(){
    return {
        email:"aniket@gmail.com",
        cnt:1,
        mname:"aniket",
        em:null,
        pass:null,
        technology : [],
        whoAmI : null,
        show:false,
        lst : ["aniket","sam","john"],
        user :[
            {name:"aniket",age:22,gender:"male"},
            {name:"sam",age:22,gender:"male"},
            {name:"ram",age:22,gender:"female"},
            {name:"kunal",age:22,gender:"male"},
            
            ],
        childUser:"eag",
        tab:"Java"
        
        }
    },

    methods:{
        getName(){
            return "Sam"
        },

        getData(){
            return{
                name : "aniket",
                email : "a@gmail.com",        
                oldemail : this.email,
                
            }
        
        },

        test(){
            this.cnt++
            alert("Function Call")
        },

        hover(){
            console.log("rhjrwhi")
        },

        onSubmit(){
            
            console.log(this.em,this.pass)
            
        },

        fun(){
            console.log("Parent function")
        },

        fun2(data){
            alert(data)
        },
        fun4(data){
            this.childUser = data
        },


    }



}
</script>

<style scoped>
    h1{
        color: red;
    }
</style>
