<template>
  <div id="app">
    
    <Titulo  :message = "title"/>
    <Campos />
    <Busca />
    <!-- <Formulario /> -->
  
  </div>
</template>

<script>

import Campos from "./components/Campos.vue";
import Titulo from "./components/Titulo.vue";
import Busca  from "./components/Busca.vue";

/* import Formulario from "./components/Formulario.vue"; */

export default {
  name: "App",
  components: {
   /*  Formulario, */
    Titulo,
    Campos, 
    Busca,
   
  },
  data : () =>({
    title: 'Cadastrar Endereco',
  }) 
};
</script>

<style>
#app {
  margin-top: 50px;
  margin-bottom: 50px;
  margin-left: 300px;
  margin-right: 300px;
  padding: 10px 50px;
}
#body {
  background: rgb(5, 22, 4);
  background: linear-gradient(
    90deg,
    rgba(5, 22, 4, 1) 1%,
    rgba(11, 34, 8, 1) 21%,
    rgba(36, 106, 5, 1) 100%
  );
}
</style>
