<template>
  <v-container>
    <v-row>
      <v-col cols="6" class="ma-auto">
        <h1>Signup</h1>
        <v-form ref="signUpForm">
          <v-text-field label="Email" type="email" v-model="email" :rules="emailRules" required/>
          <v-autocomplete label="Which browser do you use?" :items="browsers"/>
          <v-file-input label="Browse photo"/>
          <v-text-field label="Birthday" v-model="birthday" readonly />
          <v-date-picker v-model="birthday" />
          <v-checkbox label="Agree to terms & conditions" v-model="agreeToTerms" :rules="agreeToTermsRules" required />
          <v-btn type="submit" color="primary">Submit</v-btn>
          <v-btn color="warning" @click="resetValidation">Reset Validation</v-btn>
          <v-btn color="error" @click="resetForm">Reset</v-btn>
        </v-form>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: "Signup",
  data: () => ({
    email: '',
    emailRules: [
        value => !!value || 'Email is required.',
        value => value.indexOf('@') !== 0 || 'Email should have a username.',
        value => value.includes('@') || 'Email should include an @ symbol.'
    ],
    agreeToTerms: false,
    agreeToTermsRules: [
        value => !!value || 'You must agree to the terms and conditions to sign up for an account'
    ],
    birthday: '',
    browsers: ['Chrome', 'Firefox', 'Edge', 'Safari', 'Brave', 'Opera', 'Tor', 'Yandex', 'Amigo']
  }),
  methods: {
    resetValidation () {
      this.$refs.signUpForm.resetValidation()
    },
    resetForm () {
      this.$refs.signUpForm.reset()
    }
  }
}
</script>

<style scoped>

</style>
