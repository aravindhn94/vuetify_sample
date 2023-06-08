<script setup lang="ts">
import { ref } from "vue";
import InputParser from "./InputParser.vue";

const convertToMinutes = (value: number): number => value * 60;
const convertToHours = (value: number): number => value / 60;
const duration = ref(0);
</script>

<template>
  <InputParser
    :parser="convertToMinutes"
    :formatter="convertToHours"
    label="Duration (Hours)"
    variant="outlined"
    type="number"
    step="1"
    min="1"
    readonly
    v-model="duration"
  />
</template>

<style scoped></style>
