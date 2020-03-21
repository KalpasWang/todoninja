<template>
  <div class="team">
    <h1 class="display-1 grey--text">Team</h1>
    <v-container fluid class="mx-auto my-5">
      <v-row>
        <v-col cols="12" sm="6" md="4" lg="3" v-for="member in team" :key="member.name">
          <v-card z-depth="0" class="text-center my-5 mx-sm-5 mx-auto" max-width="300">
            <v-avatar size="100" class="mx-auto my-4">
                <img :src="member.avatar">
            </v-avatar>
            <v-card-title class="headline justify-center">{{ member.name }}</v-card-title>
            <v-card-subtitle>{{ member.role }}</v-card-subtitle>
            <v-card-actions>
              <v-btn text color="deep-purple">
                <v-icon small left>mdi-message</v-icon>
                <span class="">Message</span>
              </v-btn>
            </v-card-actions>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
// @ is an alias to /src


export default {
  name: 'Team',
  data() {
    return {
      team: [
        { name: 'The Net Ninja', role: 'Web developer', avatar: '/avatar-1.png' },
        { name: 'Ryu', role: 'Graphic designer', avatar: '/avatar-2.png' },
        { name: 'Chun Li', role: 'Web developer', avatar: '/avatar-3.png' },
        { name: 'Gouken', role: 'Social media maverick', avatar: '/avatar-4.png' },
        { name: 'Yoshi', role: 'Sales guru', avatar: '/avatar-5.png' }
      ]
    }
  }
}
</script>