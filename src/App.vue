<template>
  <v-app>
    <NavBar />
    <v-content>
      <v-container class="mx-6 my-5">
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
