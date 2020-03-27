<template>
  <div>
    <v-container class="my-5">
      <v-expansion-panels class="white--text">
        <v-expansion-panel v-for="project in myProjects" :key="project.title">
          <v-expansion-panel-header class="font-weight-bold info--text">{{project.title}}</v-expansion-panel-header>
          <v-expansion-panel-content>
            <v-card>
              <v-card-text class="px-4 grey--text">
                <div
                  class="font-weight-bold"
                >Due by {{ new Date(project.due_date).toUTCString().substring(0,16) }}</div>
                <div>{{project.content}}</div>
              </v-card-text>
            </v-card>
          </v-expansion-panel-content>
        </v-expansion-panel>
      </v-expansion-panels>
    </v-container>
  </div>
</template>

<script>
import db from "@/config/fb";

export default {
  name: "Projects",
  data() {
    return {
      projects: []
    };
  },
  computed: {
    myProjects() {
      return this.projects.filter(project => {
        return project.pic === "Juleshwa";
      });
    }
  },
  created() {
    db.collection("projects").onSnapshot(res => {
      const changes = res.docChanges();
      changes.forEach(change => {
        if (change.type === "added") {
          this.projects.push({
            ...change.doc.data(),
            id: change.doc.id
          });
        }
      });
    });
  }
};
</script>
