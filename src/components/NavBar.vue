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

        <v-navigation-drawer app temporary v-model="drawer" class="deep-purple accent-4">
            <p>test</p>
        </v-navigation-drawer>
    </nav>
</template>

<script>
export default {
    data() {
        return {
            drawer: false,
        };
    }
}
</script>

