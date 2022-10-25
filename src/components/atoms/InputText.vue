<script setup lang="ts">
import { ValidationRule } from "quasar";
import { defineProps } from "vue";

interface Props {
  label: string;
  mask?: string;
  rules?: Array<ValidationRule>
}



const props = defineProps<Props>();





</script>

<template>
  <q-input  unmasked-value outlined :label="props.label" standout :mask="props.mask" :rules="props.rules"> </q-input>
</template>

<style scoped></style>
