<template>
  <div>
    <Form @submit="handleSubmit" />
  </div>
</template>

<script>
import Form from "./components/Form.vue";

export default {
  name: "App",
  components: {
    Form,
  },
  methods: {
    handleSubmit(data) {
      console.log(data);
    },
  },
};
</script>
