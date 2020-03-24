<template>
    <nav>
        <v-toolbar>
            <v-app-bar-nav-icon @click ="drawer = !drawer"></v-app-bar-nav-icon>
            <v-toolbar-title class="text-uppercase grey--text">
                <span class="font-weight-light">Todo</span>
                <span>Ninja</span>
            </v-toolbar-title>
            <v-spacer></v-spacer>
            <v-menu bottom offset-y>
              <template v-slot:activator="{ on }">
                <v-btn
                  depressed
                  v-on="on"
                >
                  Menu
                </v-btn>
              </template>

              <v-list>
                <v-list-item
                  v-for="(list, index) in lists"
                  :key="index"
                  :to="list.route"
                >
                  <v-list-item-title>{{ list.text }}</v-list-item-title>
                </v-list-item>
              </v-list>
            </v-menu>
            <v-btn depressed>
                <span>Sign Out</span>    
                <v-icon right>mdi-exit-to-app</v-icon>
            </v-btn> 
        </v-toolbar>

        <v-navigation-drawer app temporary dark v-model="drawer" class="primary">
            <v-card elevation="0" class="text-center mx-auto transparent mt-5">
              <v-avatar size="100" class="mx-auto my-4">
                  <img src="/avatar-1.png">
              </v-avatar>
              <v-card-title class="headline justify-center">The Net Ninja</v-card-title>
            </v-card>
            <Popup class="mx-auto my-4"></Popup>
            <v-list>
              <v-list-item
                v-for="list in lists"
                :key="list.text"
                link
                :to="list.route"
              >

              <v-list-item-icon>
                <v-icon>{{ list.icon }}</v-icon>
              </v-list-item-icon>

              <v-list-item-content>
                <v-list-item-title>{{ list.text }}</v-list-item-title>
              </v-list-item-content>

              </v-list-item>
            </v-list>
        </v-navigation-drawer>
    </nav>
</template>

<script>
import Popup from './Popup';

export default {
    components: { Popup },
    data() {
      return {
          drawer: false,
          lists: [
            { icon: 'mdi-view-dashboard', text: 'Dashboard', route: '/'},
            { icon: 'mdi-folder-multiple', text: 'Project', route: '/project'},
            { icon: 'mdi-account-group', text: 'Team', route: '/team'},
          ]
      };
    }
}
</script>

<style scoped>
nav .v-btn {
  margin-right: 20px;
}
</style>