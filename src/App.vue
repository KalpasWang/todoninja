<template>
  <v-app class="grey lighten-4">
    <NavBar />
    <v-content class="grey lighten-4">
      <v-container class="mx-auto my-5">
        <router-view></router-view>
      </v-container>
    </v-content>
  </v-app>
</template>

<script>

import NavBar from './components/NavBar';

export default {
  name: 'App',

  components: {
    NavBar,
  },

  data: () => ({
    //
  }),
};
</script>
