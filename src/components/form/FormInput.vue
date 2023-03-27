<template>
  <div>
    <label :for="label">{{ label }}</label>
    <input
      type="text"
      :id="label"
      :value="modelValue"
      @input="$emit('update:modelValue', $event.target.value)"
    />
  </div>
</template>

<script>
export default {
  name: "FormInput",
  props: {
    label: {
      type: String,
      required: true,
    },
    modelValue: {
      type: String,
      required: true,
      default: "",
    },
  },
};
</script>
