<template>
    <nav>
        <v-toolbar flat app>
            <v-app-bar-nav-icon @click ="drawer = !drawer"></v-app-bar-nav-icon>
            <v-toolbar-title class="text-uppercase grey--text">
                <span class="font-weight-light">Todo</span>
                <span>Ninja</span>
            </v-toolbar-title>
            <v-spacer></v-spacer>
            <v-btn depressed>
                <span>Sign Out</span>    
                <v-icon right>mdi-exit-to-app</v-icon>
            </v-btn> 
        </v-toolbar>

        <v-navigation-drawer app temporary dark v-model="drawer" class="primary">
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
export default {
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

