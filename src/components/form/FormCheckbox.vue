<template>
  <div>
    <label :for="label">{{ label }}</label>
    <input
      type="checkbox"
      :id="label"
      :checked="modelValue"
      @input="$emit('update:modelValue', $event.target.checked)"
    />
  </div>
</template>

<script>
export default {
  name: "FormCheckbox",
  props: {
    label: {
      type: String,
      required: true,
    },
    modelValue: {
      type: Boolean,
      required: true,
      default: false,
    },
  },
};
</script>
