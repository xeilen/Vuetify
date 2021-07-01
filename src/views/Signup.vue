<template>
  <v-container>
    <v-row>
      <v-col cols="6" class="ma-auto">
        <h1>Signup</h1>
        <v-form>
          <v-text-field label="Email" type="email" />
          <v-autocomplete label="Which browser do you use?" :items="browsers"/>
          <v-file-input label="Browse photo"/>
          <v-text-field label="Birthday" v-model="birthday" readonly />
          <v-date-picker v-model="birthday" />
          <v-checkbox label="Agree to terms & conditions"/>
          <v-btn type="submit" color="primary">Submit</v-btn>
        </v-form>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: "Signup",
  data: () => ({
    birthday: '',
    browsers: ['Chrome', 'Firefox', 'Edge', 'Safari', 'Brave', 'Opera', 'Tor', 'Yandex', 'Amigo']
  })
}
</script>

<style scoped>

</style>
