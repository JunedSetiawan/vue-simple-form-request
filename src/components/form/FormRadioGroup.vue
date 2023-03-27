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
        :class="{ 'is-invalid': error }"
      />
      <label :for="option">{{ option }}</label>
      <div v-if="error" class="invalid-feedback">{{ error }}</div>
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
    error: {
      type: String,
      default: "",
    },
  },
};
</script>
