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
            <v-text-field 
              v-model="title" 
              :error-messages="titleErrors"
              label="Title" 
              required 
              prepend-icon="mdi-folder"
              @input="$v.title.$touch()"
              @blur="$v.title.$touch()"
            ></v-text-field>
            <v-textarea 
              v-model="content" 
              :error-messages="contentErrors"
              label="Information" 
              required 
              :counter="5" 
              prepend-icon="mdi-pencil"
              @input="$v.content.$touch()"
              @blur="$v.content.$touch()"
            ></v-textarea>
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
                  :error-messages="dateErrors"
                  label="Date"
                  prepend-icon="mdi-calendar"
                  required
                  readonly
                  v-on="on"
                  @input="$v.date.$touch()"
                  @blur="$v.date.$touch()"
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
          <v-btn color="success" text @click="clear">Clear</v-btn>
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
import { validationMixin } from 'vuelidate'
import { required, minLength } from 'vuelidate/lib/validators'

export default {
  mixins: [validationMixin],

  validations: {
    title: { required },
    content: { 
      required, 
      minLength: minLength(5) 
    },
    date: { required }
  },

  data() {
    return {
      dialog: false,
      title: '',
      content: '',
      date: null,
      menuDatePicker: false
    }
  },

  computed: {
    titleErrors () {
      const errors = [];
      if (!this.$v.title.$dirty) return errors;
      !this.$v.title.required && errors.push('Title is required.');
      return errors;
    },
    contentErrors () {
      const errors = [];
      if (!this.$v.content.$dirty) return errors;
      !this.$v.content.required && errors.push('Content is required.');
      !this.$v.content.minLength && errors.push('Infomation must at least have 5 characters.');
      return errors;
    },
    dateErrors () {
      const errors = [];
      if (!this.$v.date.$dirty) return errors;
      !this.$v.date.required && errors.push('Date is required.');
      return errors;
    }
  },

  methods: {
    submit() {
      this.$v.$touch();
      if(!this.$v.$invalid) {
        this.dialog = false;
        alert(`${this.title}\n${this.content}\n${this.date}`);
      }
    },
    clear () {
      this.$v.$reset();
      this.title = '';
      this.content = '';
      this.date = null;
    },
  }
}
</script>

<style scoped>

</style>