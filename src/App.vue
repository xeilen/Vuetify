<template>
  <v-app>
    <v-app-bar app color="primary" dark>
      <v-toolbar-title>Vuetify Dashboard</v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn
          v-for="link in links"
          :key="`${link.label}-header-link`"
          color="white"
          text
          rounded
          class="my-2"
          :to="link.url"
      >
        {{ link.label }}
      </v-btn>
<!--      <v-btn text rounded to="/">Home</v-btn>-->
<!--      <v-btn text rounded to="/login">Login</v-btn>-->
    </v-app-bar>
    <v-content>
      <!-- Login Module -->
<!--      <Login />-->
      <router-view></router-view>
    </v-content>
    <v-footer color="primary lighten-1" padless>
      <v-layout justify-center wrap>
        <v-btn
            v-for="link in links"
            :key="`${link.label}-footer-link`"
            color="white"
            text
            rounded
            class="my-2"
            :to="link.url"
        >
          {{ link.label }}
        </v-btn>
        <v-flex primary lighten-2 py-4 text-center white--text xs12>
          {{ new Date().getFullYear() }} — <strong>Vuetify Dashboard</strong>
        </v-flex>
      </v-layout>
    </v-footer>
  </v-app>
</template>

<script>

export default {
  name: 'App',

  components: {
  },

  data: () => ({
    links: [
      {
        label: 'Home',
        url: '/',
      },
      {
        label: 'Login',
        url: '/login'
      },
      {
        label: 'Signup',
        url: '/signup'
      },
      {
        label: 'Dashboard',
        url: '/dashboard'
      }
    ]
  }),
};
</script>
