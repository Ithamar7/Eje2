<template>
  <div class="hello">
    <h3>(props): {{ msg }}</h3>
    <h4>(data): {{textoMostrar}}</h4>
    <h4>(methods): {{mensaje()}}</h4>
    <h4>(computed): {{cadena}}</h4>
    <!-- <input @input="ejecutarInput" />
    <input v-model="textoMostrar"/> -->
    <hr>
    <input :value="textoMostrar" /> 
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String,
  },
  data(){
    return{
      textoMostrar: "Hola! desde data"
    }
  },
  methods:{
    mensaje(){
      return "Mensaje de methods";
    },
    ejecutarInput(e){
      this.textoMostrar = e.target.value
    }
  },
  computed:{  ///los computed son funciones como methods, que se mantienen en cache
    cadena(){
      return "Saludo: " + this.textoMostrar;
    }
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
