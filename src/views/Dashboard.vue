<template>
  <div class="dashboard">
    <h1 class="display-1 grey--text">Dashboard</h1>
    <v-container fluid class="my-5"> 
      <v-card flat v-for="project in projects" :key="project.title">
        <v-row color="grey" :class="`project ${project.status}`">
          <v-col md="6" sm="12">
            <div class="caption grey--text">Project Title</div>
            <div>{{ project.title }}</div>
          </v-col>
          <v-col md="2" sm="6">
            <div class="caption grey--text">Person</div>
            <div>{{ project.person }}</div>
          </v-col>
          <v-col md="2" sm="6">
            <div class="caption grey--text">Due Date</div>
            <div>{{ project.due }}</div>
          </v-col>
          <v-col md="2" sm="12">
            <div class="caption grey--text">Status</div>
            <div>{{ project.status }}</div>
          </v-col>
        </v-row>
        <v-divider></v-divider>
      </v-card>
    </v-container>
  </div>
</template>

<script>
// @ is an alias to /src


export default {
  name: 'Dashboard',
  data() {
    return {
      projects: [
        { title: 'Design a new website', person: 'The Net Ninja', due: '1st Jan 2019', status: 'ongoing', content: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Sunt consequuntur eos eligendi illum minima adipisci deleniti, dicta mollitia enim explicabo fugiat quidem ducimus praesentium voluptates porro molestias non sequi animi!'},
        { title: 'Code up the homepage', person: 'Chun Li', due: '10th Jan 2019', status: 'complete', content: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Sunt consequuntur eos eligendi illum minima adipisci deleniti, dicta mollitia enim explicabo fugiat quidem ducimus praesentium voluptates porro molestias non sequi animi!'},
        { title: 'Design video thumbnails', person: 'Ryu', due: '20th Dec 2018', status: 'complete', content: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Sunt consequuntur eos eligendi illum minima adipisci deleniti, dicta mollitia enim explicabo fugiat quidem ducimus praesentium voluptates porro molestias non sequi animi!'},
        { title: 'Create a community forum', person: 'Gouken', due: '20th Oct 2018', status: 'overdue', content: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Sunt consequuntur eos eligendi illum minima adipisci deleniti, dicta mollitia enim explicabo fugiat quidem ducimus praesentium voluptates porro molestias non sequi animi!'},
      ]
    }
  }
}
</script>


<style scoped>
.project {
  box-sizing: border-box;
}

.project.ongoing {
  border-left: 4px #43a047 solid;
}

.project.complete {
  border-left: 4px #546e7a solid;
}

.project.overdue {
  border-left: 4px #e53935 solid;
}

</style>