<template>

  <div id='div1' class="hello">

  <div>
    <img  id="img" src="https://fontmeme.com/images/Pokemon-Logo.jpg">

     
    
    
</div>


   <input type="text" id="pokeID"  placeholder="numéro du pokémon">
   
  <img   v-on:click="recherchepoke"  class="animate__animated animate__bounce animate__infinite animate__fast"  width="30" height="30" id="pokeball" src="..\assets\Poké_Ball_icon.svg.png">


<ul id="list">
<div>ID : {{this.info.id}} </div>
<div> Name:{{this.info.name}} </div>
<li v-for="value in this.info.types">
     Type:{{ value.type.name }}
</li>
<div> Taile : {{this.info.height}} cm </div>
<div> <img id="pokimage"></img> <img id="pokishiny"></img> </div>

     
 
</ul>


</div>

</template>

<script>
import 'animate.css';
import axios from 'axios';
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      info: null,
    
     
    }
  },
  methods: {
   
    recherchepoke: function(){
      var url= document.getElementById("pokeID").value
       axios
      .get('https://pokeapi.co/api/v2/pokemon/'+ url)
      .then(response => {
        this.info = response.data
        var pokimage = document.getElementById('pokimage')
        var pokishiny = document.getElementById('pokishiny')
       pokimage.src = this.info.sprites.front_default
       pokishiny.src= this.info.sprites.front_shiny
      
       
      
      })
    },
    },
 mounted () {
    axios
      .get('https://pokeapi.co/api/v2/pokemon/')
      .then(response => {
        this.info = response.data
        

       
      
      })
  }
}
 



</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
   background-image: url('..\vuetest\src\assets\pokedex.jpg')
  
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
