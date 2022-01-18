<template>
  <br><br><br>
    <p v-if="err.length">
        <b>Please correct the following error(s):</b>
        <ul>
            <li v-for="error in err" :key="error">{{ error }} is  invalid</li>
        </ul>
    </p>

<form @submit.prevent="getData">
    <input type="text" name="" id="" placeholder="Email" v-model="form.email"><br>
    <!-- <div v-if="err.email">please Add Email<br></div> -->
    <input type="text" name="" id="" placeholder="Password" v-model="form.password"><br>
    
    <select name="" id="" v-model="form.country">
        <option value="India" selected>India</option>
        <option value="China">China</option>
        <option value="USA">Usa</option>
    </select> <br><br>
    
    <h3>technology</h3>
    
    <label for="java">Java</label>
    <input type="checkbox" name="ja" id="java" value="java" v-model="form.technology">
    
    <label for="py">Python</label>
    <input type="checkbox" name="p" id="py" value="python" v-model="form.technology">
    
    <label for="js">Js</label>
    <input type="checkbox" name="js" id="js" value="javascript" v-model="form.technology">
    
    
    <br><br><br>
    Select Gender
    <select name="" id="" v-model="form.gender">
        <option  selected disabled>Select Options</option>
        <option value="male">Male</option>
        <option value="female">Female</option>
       
    </select> <br><br>


    <button type="submit">Login</button>
</form>
    {{form}}
    <br>

    EMAIL IS {{getName}}
    <br>
    <br>
    <br>

    {{cnt}}
    <button v-on:click="cnt++"> + </button> &nbsp; 
    <button v-on:click="cnt--"> - </button>  


</template>
<script>
export default {
 name:"MyForm",

 data(){
    return {
        form:{
            email:"",
            password:"",
            country:"",
            technology:[],
            gender:""
        },
        err:[],
        cnt:0,
    }
 },
 methods:{
     getData(){
        this.err = [] // validation
        for(let i in this.form){
            if(this.form[i]===''|| this.form[i].length===0){
                this.err.push(i)
            } 
            else if(i == "email"){
                var re = /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
                if(! re.test(this.form.email)){
                    this.err.push(i)
                   
                }
                
            } 
            
            
        }
 
        
        if(this.err.length === 0){
            alert("Data has been Submited..!")
        }  
        
        console.log(this.form)
      }
    },
    computed:{  // computed properties are cached based on their reactive dependencies
        getName(){
            return this.form.email
        }
    },
    watch:{
        cnt(val,prev){  // current value 
            console.log("cnt is changing ",val,"and previsous value was ",prev)
        }
    }

}
</script>