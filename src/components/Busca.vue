<template>
  <div>
    <b-card class="mt-3" header="Busca requisição via cep ">
      <h5 id = "titulo">Busca Processada .......</h5>
      <hr>
      <p>CEP: {{ cep }}</p>
      <hr>
      <p>LOGRADOURO: {{ logradouro }}</p>
      <hr>
      <p>BAIRRO: {{ bairro }}</p>
      <hr>
      <p>UF: {{ uf }}</p>
      <hr>
      <p>IBGE: {{ ibge }}</p>
      <hr>
      <p>DDD: {{ ddd }}</p>
      <hr>
      <p>SIAFI: {{ siafi }}</p>
    </b-card>
  </div>
</template>

<script>
import B from "../importvue";

export default {
  data: () => ({
    cep: "",
    logradouro:"",
    bairro:"",
    uf:"",
    ibge:"",
    ddd:"",
    siafi:"",
  }),
  mounted() {
    B.$on("update-cep", (value) => this.cep = value);
    B.$on("update-logradouro", (valeu2)=> this.logradouro = valeu2);
    B.$on("update-bairro", (value3)=> this.bairro = value3);
    B.$on("update-uf", (value4)=> this.uf = value4);
    B.$on("update-ibge", (value5)=>this.ibge = value5);
    B.$on("update-ddd", (value6) => this.ddd = value6);
    B.$on("update-siafi", (value7) => this.siafi = value7);
  },
};
</script>

<style scoped>
#titulo{
  text-align: center;
}


</style>
