<template>
  <div class="row g-3 needs-validation border border-dark d-block p-3">
    <h2>Form Pendaftaran</h2>
    <div class="d-flex flex-column align-items-start">
      <FormInput
        class="my-2"
        label="Name : "
        v-model="name"
        :error="formErrors.name"
      />
      <FormRadioGroup
        label="Jenis Kelamin :"
        v-model="gender"
        :options="genderOptions"
        :error="formErrors.gender"
      />
      <FormSelect
        class="my-2"
        label="Kota : "
        v-model="city"
        :options="cityOptions"
      />
      <FormCheckbox label="setuju untuk persyaratan " v-model="agreeToTerms" />
      <button :disabled="!agreeToTerms" @click="submitForm" class="btn btn-primary mt-2">Submit</button>
      <span class="text-secondary mt-2">* hasil bisa dilihat di console</span>
    </div>
  </div>
</template>

<script>
import FormInput from "./form/FormInput.vue";
import FormRadioGroup from "./form/FormRadioGroup.vue";
import FormSelect from "./form/FormSelect.vue";
import FormCheckbox from "./form/FormCheckbox.vue";

export default {
  name: "Form",
  components: {
    FormInput,
    FormRadioGroup,
    FormSelect,
    FormCheckbox,
  },
  data() {
    return {
      name: "",
      gender: "",
      genderOptions: ["Male", "Female"],
      city: "",
      cityOptions: ["Jakarta", "Bandung", "Surabaya"],
      agreeToTerms: false,
      formErrors: {},
    };
  },
  methods: {
    submitForm() {
      // Validate form before submitting
      this.formErrors = {};
      if (!this.name) {
        this.formErrors.name = "nama harus diisi";
      }
      if (!this.gender) {
        this.formErrors.gender = "jenis kelamin harus diisi";
      }

      // If there are no errors, emit form data to parent component
      if (Object.keys(this.formErrors).length === 0) {
        this.$emit("submit", {
          name: this.name,
          gender: this.gender,
          city: this.city,
          agreeToTerms: this.agreeToTerms,
        });
      }
    },
  },
};
</script>
