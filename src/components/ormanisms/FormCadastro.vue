<script setup lang="ts">
import { ref } from "vue";
import InputText from "../atoms/InputText.vue";
import InputSubmit from "../atoms/InputSubmit.vue";
import IFormCadastro from "../../shared/models/IFormCadastro.model";

const data = ref<IFormCadastro>({
  name: "",
  email: "",
  phone: "",
  cpf: "",
});

function isEmpty(val: string): boolean | string {
  return !!val || "Campo obrigatorio!";
}

function isEmailValid(val: string): boolean | string {
  const emailPattern = /^(?=[a-zA-Z0-9@._%+-]{6,254}$)[a-zA-Z0-9._%+-]{1,64}@(?:[a-zA-Z0-9-]{1,63}\.){1,8}[a-zA-Z]{2,63}$/;
  return emailPattern.test(val) || "Insira um email valido!";
}

function isPhoneValid(val: string): boolean | string {
  return val.length === 11 || "Insira um telefone valido!";
}

function isCpfValid(val: string): boolean | string {
  return val.length === 11 || "Insira um telefone valido!";
}

const onSubmit = () => {
  console.log(data.value);
};
</script>

<template>
  <q-form dense q-pa-lg class="row" @submit="onSubmit">
    <input-text
      class="col-md-12 col-xs-12"
      label="Nome completo"
      v-model="data.name"
      :rules="[isEmpty]"
    >
    </input-text>

    <input-text
      class="col-md-12 col-xs-12"
      label="Email"
      v-model="data.email"
      :rules="[isEmpty, isEmailValid]"
    >
    </input-text>

    <input-text
      class="col-md-6 col-sm-6 col-xs-12"
      label="Telefone"
      v-model="data.phone"
      mask="(##) # ####-####"
      :rules="[isEmpty, isPhoneValid]"
    >
    </input-text>

    <input-text
      class="col-md-6 col-sm-6 col-xs-12"
      label="CPF"
      v-model="data.cpf"
      mask="###.###.###-##"
      :rules="[isEmpty, isCpfValid]"
    ></input-text>
    <input-submit class="col-12" label="Cadastrar"></input-submit>
  </q-form>
</template>

<style scoped></style>
