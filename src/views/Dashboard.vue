<template>
  <div class="dashboard">
    <h1 class="display-1 grey--text">Dashboard</h1>
    <v-container fluid class="mx-auto my-5"> 
      
      <div class="options mx-auto mb-5">
        <v-menu offset-y>
          <template v-slot:activator="{ on }">
            <v-btn v-on="on" transparent depressed>
              <v-icon left>mdi-sort</v-icon>
              Order By
              <v-icon>mdi-menu-down</v-icon>
            </v-btn>
          </template>
          <v-list>
            <v-list-item
              v-for="(item, index) in sortings"
              :key="index"
              @click="sortBy(item.prop)"
            >
              <v-list-item-title>{{ item.title }}</v-list-item-title>
            </v-list-item>
          </v-list>
        </v-menu>
      </div>

      <div v-if="show" id="projects">
        <v-alert v-for="project in projects" :key="project.title" width="90%" border="left" 
          colored-border :color="`${colors[project.status]}`" elevation="2" class="py-0 mx-auto"
        >
          <v-row>
            <v-col cols="12" sm="12" md="6">
              <div class="caption grey--text">Project Title</div>
              <div>{{ project.title }}</div>
            </v-col>
            <v-col cols="6" sm="4" md="2">
              <div class="caption grey--text">Person</div>
              <div>{{ project.person }}</div>
            </v-col>
            <v-col cols="6" sm="4" md="2">
              <div class="caption grey--text">Due Date</div>
              <div>{{ project.due }}</div>
            </v-col>
            <v-col cols="6" sm="4" md="2">
              <div class="caption grey--text">Status</div>
              <v-chip class="ma-2" :color="`${colors[project.status]}`" text-color="white">
                <v-avatar left>
                  <v-icon>{{ icons[project.status] }}</v-icon>
                </v-avatar>
                {{ project.status }}
              </v-chip>
            </v-col>
          </v-row>
        </v-alert>
      </div>
      <div v-else id="loading" class="mx-auto my-5">
        <img class="d-block mx-auto my-5" src="../assets/spinner2.gif">
      </div>
      
    </v-container>
  </div>
</template>

<script>
// @ is an alias to /src


export default {
  name: 'Dashboard',
  data() {
    return {
      show: true,
      projects: [
        { title: 'Design a new website', person: 'The Net Ninja', due: '1st Jan 2019', status: 'ongoing', content: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Sunt consequuntur eos eligendi illum minima adipisci deleniti, dicta mollitia enim explicabo fugiat quidem ducimus praesentium voluptates porro molestias non sequi animi!'},
        { title: 'Code up the homepage', person: 'Chun Li', due: '10th Jan 2019', status: 'complete', content: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Sunt consequuntur eos eligendi illum minima adipisci deleniti, dicta mollitia enim explicabo fugiat quidem ducimus praesentium voluptates porro molestias non sequi animi!'},
        { title: 'Design video thumbnails', person: 'Ryu', due: '20th Dec 2018', status: 'complete', content: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Sunt consequuntur eos eligendi illum minima adipisci deleniti, dicta mollitia enim explicabo fugiat quidem ducimus praesentium voluptates porro molestias non sequi animi!'},
        { title: 'Create a community forum', person: 'Gouken', due: '20th Oct 2018', status: 'overdue', content: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Sunt consequuntur eos eligendi illum minima adipisci deleniti, dicta mollitia enim explicabo fugiat quidem ducimus praesentium voluptates porro molestias non sequi animi!'},
      ],
      icons: {
        ongoing: 'mdi-run',
        complete: 'mdi-check',
        overdue: 'mdi-alarm-off'
      },
      colors: {
        ongoing: 'green ligthen-3',
        complete: 'indigo lighten-3',
        overdue: 'red lighten-1'
      },
      sortings: [
        { title: 'By Person', prop: 'title' },
        { title: 'By Project', prop: 'person' }
      ]
    }
  },

  methods: {
    sortBy(prop) {
      this.show = false;
      let self = this;
      setTimeout(function() {
        self.projects.sort((a,b) => a[prop] < b[prop] ? -1 : 1);
        self.show = true;
      }, 1000);
    }
  }
}
</script>


<style scoped>
.project.ongoing {
  border-left: 4px #43a047 solid;
}

.project.complete {
  border-left: 4px #546e7a solid;
}

.project.overdue {
  border-left: 4px #e53935 solid;
}

.v-chip.complete{
  background: #3cd1c2;
}
.v-chip.ongoing{
  background: #ffaa2c;
}
.v-chip.overdue{
  background: #f83e70;
}

.options {
  width: 90%;
}
</style>