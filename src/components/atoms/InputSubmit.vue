<script setup lang="ts">
import { defineProps } from 'vue';
interface Props {
  label: string
}

const props = defineProps<Props>()

</script>


<template>
  <q-btn color="teal" :elevated="false" :label="props.label" type="submit"></q-btn>
</template>


<style scoped>

</style>
