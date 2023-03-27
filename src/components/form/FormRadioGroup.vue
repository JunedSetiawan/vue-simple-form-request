<template>
  <div>
    <label>{{ label }}</label>
    <div v-for="option in options" :key="option">
      <input
        type="radio"
        :id="option"
        :value="option"
        :checked="option === modelValue"
        @change="$emit('update:modelValue', option)"
      />
      <label :for="option">{{ option }}</label>
    </div>
  </div>
</template>
<script>
export default {
  name: "FormRadioGroup",
  props: {
    label: {
      type: String,
      required: true,
    },
    modelValue: {
      type: String,
      required: true,
    },
    options: {
      type: Array,
      required: true,
    },
  },
};
</script>
