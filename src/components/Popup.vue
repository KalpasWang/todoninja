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
          <!-- <v-spacer></v-spacer> -->
          <v-menu
            ref="menu"
            v-model="menuDatePicker"
            :close-on-content-click="false"
            transition="scale-transition"
            offset-y
            min-width="290px"
          >
            <template v-slot:activator="{ on }">
              <v-text-field
                v-model="date"
                label="Date"
                prepend-icon="mdi-calendar"
                readonly
                v-on="on"
              ></v-text-field>
            </template>
            <v-date-picker v-model="date" no-title scrollable>
              <v-spacer></v-spacer>
              <v-btn text color="primary" @click="menuDatePicker = false">Cancel</v-btn>
              <v-btn text color="primary" @click="$refs.menu.save(date)">OK</v-btn>
            </v-date-picker>
          </v-menu>
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
      content: '',
      date: null,
      menuDatePicker: false
    }
  },
  methods: {
    submit() {
      this.dialog = false;
      alert(`${this.title}\n${this.content}\n${this.date}`);
    }
  }
}
</script>

<style scoped>

</style>