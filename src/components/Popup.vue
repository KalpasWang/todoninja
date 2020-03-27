<template>
  <div class="text-center">
    <v-dialog
      v-model="dialog"
      width="80%"
      max-width="500"
    >
      <template v-slot:activator="{ on }">
        <v-btn
          class="teal darken-1"
          dark
          v-on="on"
        >
          Create Project
        </v-btn>
      </template>

      <v-card>
        <v-card-title
          class="headline grey lighten-2"
          primary-title
        >
          Add a New Project
        </v-card-title>

        <v-card-text>
          <v-form class="px-3">
          <v-text-field v-model="title" label="Title" prepend-icon="mdi-folder"></v-text-field>
          <v-textarea v-model="content" label="Information" prepend-icon="mdi-pencil"></v-textarea>
          <v-spacer></v-spacer>
          <!-- <v-btn flat @click="submit" class="success mx-0 mt-3">Add Project</v-btn> -->
        </v-form>
        </v-card-text>

        <v-divider></v-divider>

        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn
            color="success"
            text
            @click="submit"
          >
            Add Project
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </div>
</template>

<script>
export default {
  data() {
    return {
      dialog: false,
      title: '',
      content: ''
    }
  },
  methods: {
    submit() {
      this.dialog = false;
      alert(`${this.title}\n${this.content}`);
    }
  }
}
</script>

<style scoped>

</style>