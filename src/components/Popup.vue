<template>
  <v-dialog max-width="400" v-model="dialog">
    <template v-slot:activator="{on}">
      <v-btn v-on="on" class="success">Add New Project</v-btn>
    </template>
    <v-card>
      <v-card-title>Add New Project</v-card-title>
      <v-card-text>
        <v-form class="px-3" ref="form">
          <v-text-field label="Title" v-model="title" prepend-icon="mdi-folder" :rules="titleRules"></v-text-field>
          <v-textarea
            :rules="contentRules"
            label="Information"
            v-model="content"
            prepend-icon="mdi-pencil"
          ></v-textarea>
          <!-- Datepicker -->
          <v-menu>
            <template v-slot:activator="{on}">
              <v-text-field
                :value="formattedDate"
                v-on="on"
                label="Due Date"
                prepend-icon="mdi-calendar"
              ></v-text-field>
            </template>
            <v-date-picker v-model="due_date"></v-date-picker>
          </v-menu>

          <v-btn text class="success mx-0 mt-3" @click="submit" :loading="loading">Add Project</v-btn>
        </v-form>
      </v-card-text>
    </v-card>
  </v-dialog>
</template>

<script>
import db from "../config/fb";

export default {
  name: "Popup",
  data() {
    return {
      title: "",
      content: "",
      due_date: null,
      titleRules: [
        title => title.length >= 3 || `Minimum title is 3 characters long.`
      ],
      contentRules: [
        content =>
          content.length >= 15 || `Minimum content is 15 characters long.`
      ],
      loading: false,
      dialog: false
    };
  },
  methods: {
    submit() {
      if (this.$refs.form.validate()) {
        this.loading = true;
        const payload = {
          title: this.title,
          content: this.content,
          due_date: this.due_date,
          pic: "Juleshwa",
          status: "Ongoing"
        };
        db.collection("projects")
          .add(payload)
          .then(() => {
            this.loading = false;
            this.dialog = false;
            this.$emit("projectAdded");
            this.title = "";
            this.content = "";
            this.due_date = null;
            console.log(`added`);
          })
          .catch(err => {
            console.log(err);
          });
      }
    }
  },
  computed: {
    formattedDate() {
      return this.due_date
        ? new Date(this.due_date).toUTCString().substring(0, 16)
        : "";
    }
  }
};
</script>