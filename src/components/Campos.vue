<template>
  <div>
    <b-form @submit="onSubmit" @reset="onReset" v-if="show">
      <b-form-group id="label" label="Cep">
        <b-form-input v-model="form.cep"></b-form-input>
      </b-form-group>
      <b-form-group id="label" label="Logradouro">
        <b-form-input v-model="form.logradouro"></b-form-input>
      </b-form-group>
      <b-form-group id="label" label="Bairro">
        <b-form-input v-model="form.bairro"></b-form-input>
      </b-form-group>
      <b-form-group id="label" label="Localidade">
        <b-form-input v-model="form.localidade"></b-form-input>
      </b-form-group>
      <b-form-group id="label" label="uf">
        <b-form-input v-model="form.uf"></b-form-input>
      </b-form-group>
      <b-form-group id="label" label="ibge">
        <b-form-input v-model="form.ibge"></b-form-input>
      </b-form-group>
      <b-form-group id="label" label="ddd">
        <b-form-input v-model="form.ddd"></b-form-input>
      </b-form-group>
      <b-form-group id="label" label="siafi">
        <b-form-input v-model="form.siafi"></b-form-input>
      </b-form-group>
      <b-button id="btnsubmit" type="submit" variant="primary">Pesquisar</b-button>
      <b-button id="btnreset" type="reset" variant="danger">Limpar</b-button>
    </b-form>
  </div>
</template>

<script>
import axios from "axios";
import B from "../importvue";

export default {
  data() {
    return {
      form: {
        cep: "",
        logradouro: "",
        complemento: "",
        bairro: "",
        localidade: "",
        uf: "",
        ibge: "",
        gia: "",
        ddd: "",
        siafi: "",
      },
      show: true,
    };
  },
  methods: {
    onSubmit(evt) {
      evt.preventDefault();
      axios
        .get(`https://viacep.com.br/ws/` + this.form.cep + `/json/`)
        .then((response) => {
          this.form.cep = response.data.cep;
          this.form.logradouro = response.data.logradouro;
          this.form.complemento = response.data.complemento;
          this.form.bairro = response.data.bairro;
          this.form.localidade = response.data.localidade;
          this.form.uf = response.data.uf;
          this.form.ibge = response.data.ibge;
          this.form.gia = response.data.gia;
          this.form.ddd = response.data.ddd;
          this.form.siafi = response.data.siafi;

          B.$emit("update-cep", response.data.cep);
          B.$emit("update-logradouro", response.data.logradouro);
          B.$emit("update-bairro", response.data.bairro);
          B.$emit("update-uf", response.data.uf);
          B.$emit("update-ibge", response.data.ibge);
          B.$emit("update-ddd", response.data.ddd);
          B.$emit("update-siafi", response.data.siafi);
        })
        .catch((e) => {
          this.errors.push(e);
        });
    },
    onReset(evt) {
      evt.preventDefault();
      this.form.cep = "";
      this.form.logradouro = "";
      this.form.complemento = "";
      this.form.bairro = "";
      this.form.localidade = "";
      this.form.uf = "";
      this.form.ibge = "";
      this.form.gia = "";
      this.form.ddd = "";
      this.form.siafi = "";
      
      B.$emit("update-cep", "");
      B.$emit("update-logradouro", "");
      B.$emit("update-bairro", "");
      B.$emit("update-uf", "");
      B.$emit("update-ibge","");
      B.$emit("update-ddd", "");
      B.$emit("update-siafi", "");

    },
  },
};
</script>

<style scoped>
#btnsubmit {
  margin: 6px;
}
h3 {
  color: white;
}

#label {
  color: white;
}
</style>
