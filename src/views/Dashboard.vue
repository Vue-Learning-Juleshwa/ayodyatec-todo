<template>
  <div>
    <v-container class="my-5">
      <!-- <v-tooltip bottom>
        <template v-slot:activator="{ on }">
          <v-btn v-on="on" color="primary" dark>Button</v-btn>
        </template>
        <span>Tooltip</span>
      </v-tooltip>-->
      <v-row class="mb-3">
        <v-tooltip top>
          <template v-slot:activator="{ on }">
            <v-btn v-on="on" small text color="teal" @click="sortBy('title')">
              <v-icon>mdi-folder</v-icon>
              <span class="caption">By Project NAME</span>
            </v-btn>
          </template>
          <span>Sort Projects By Name</span>
        </v-tooltip>
        <v-tooltip top>
          <template v-slot:activator="{on}">
            <v-btn v-on="on" small text color="teal" @click="sortBy('pic')">
              <v-icon>mdi-account</v-icon>
              <span class="caption">By PIC</span>
            </v-btn>
          </template>
          <span>Sort Projects By PIC</span>
        </v-tooltip>
      </v-row>
      <v-card class="px-3" v-for="project in projects" :key="project.title">
        <v-row wrap :class="`pa-3 project ${project.status}`">
          <v-col cols="12" md="6">
            <div class="caption grey--text">Project Title</div>
            <div>{{project.title}}</div>
          </v-col>
          <v-col cols="6" md="2" sd="4">
            <div class="caption grey--text">Person</div>
            <div>{{project.pic}}</div>
          </v-col>
          <v-col cols="6" md="2" sd="4">
            <div class="caption grey--text">Due Date</div>
            <div>{{project.due_date}}</div>
          </v-col>
          <v-col cols="2" md="2" sd="4">
            <div class="right">
              <v-chip
                small
                :color="`${project.status}`"
                :class="`v-chip--active caption white--text my-2`"
              >{{project.status}}</v-chip>
            </div>
          </v-col>
        </v-row>
        <v-divider></v-divider>
      </v-card>
    </v-container>
  </div>
</template>

<script>
// @ is an alias to /src
import db from "@/config/fb";

export default {
  name: "Dashboard",
  components: {},
  data() {
    return {
      projects: []
    };
  },
  methods: {
    sortBy(prop) {
      this.projects.sort((a, b) => (a[prop] < b[prop] ? -1 : 1));
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

<style>
.project.Completed {
  border-left: solid 4px #3cd1c2;
}
.project.Ongoing {
  border-left: solid 4px orange;
}
.project.Overdue {
  border-left: solid 4px red;
}
.v-chip.Completed {
  background: #3cd1c2;
}
.v-chip.Ongoing {
  background-color: orange;
}
.v-chip.Overdue {
  background-color: red;
}

.right {
  text-align: right;
}
</style>
