<script
  setup
  lang="ts"
  generic="TValue, TFormattedValue extends string | number"
>
import { ExtractPropTypes, computed } from "vue";
import { VTextField } from "vuetify/components";

const props = defineProps<
  {
    modelValue: TValue;
    parser: (value: TFormattedValue) => TValue;
    formatter: (value: TValue) => TFormattedValue;
  } & Partial<ExtractPropTypes<VTextField>>
>();

const emit = defineEmits(["update:modelValue"]);

const value = computed({
  get() {
    return props.formatter(props.modelValue);
  },

  set(value) {
    emit("update:modelValue", props.parser(value));
  },
});
</script>

<template>
  <VTextField v-model="value" v-bind="$attrs" />
</template>
