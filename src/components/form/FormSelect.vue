<template>
  <div>
    <label :for="label">{{ label }}</label>
    <select
      :id="label"
      :value="modelValue"
      @input="$emit('update:modelValue', $event.target.value)"
    >
      <option v-for="option in options" :key="option" :value="option">
        {{ option }}
      </option>
    </select>
  </div>
</template>

<script>
export default {
  name: "FormSelect",
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
