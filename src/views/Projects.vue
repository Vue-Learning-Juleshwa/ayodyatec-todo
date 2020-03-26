<template>
  <div>
    <h1 class="subtitle-1 grey--text">This is an projects page</h1>
    <v-container class="my-5">
      <v-expansion-panels class="white--text">
        <v-expansion-panel v-for="project in myProjects" :key="project.title">
          <v-expansion-panel-header class="font-weight-bold info--text">{{project.title}}</v-expansion-panel-header>
          <v-expansion-panel-content>
            <v-card>
              <v-card-text class="px-4 grey--text">
                <div class="font-weight-bold">Due by {{project.due_date}}</div>
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
export default {
  name: "Projects",
  data() {
    return {
      projects: [
        {
          title: "Design Portfolios for Remote Job",
          pic: "Micha",
          due_date: "28 February 2020",
          status: "Overdue",
          content:
            "Lorem ipsum dolor sit amet consectetur adipisicing elit. Nam accusantium perferendis laboriosam deserunt cum, voluptas nisi at totam veritatis nesciunt iste aspernatur nobis officiis laudantium dolore autem quo eum maiores."
        },
        {
          title: "Setting Homepage for Learn2Code",
          pic: "Juleshwa",
          due_date: "26 March 2020",
          status: "Completed",
          content:
            "Lorem ipsum dolor sit amet consectetur adipisicing elit. Nam accusantium perferendis laboriosam deserunt cum, voluptas nisi at totam veritatis nesciunt iste aspernatur nobis officiis laudantium dolore autem quo eum maiores."
        },
        {
          title: "Learning React Native",
          pic: "Bluebell",
          due_date: "28 June 2020",
          status: "Ongoing",
          content:
            "Lorem ipsum dolor sit amet consectetur adipisicing elit. Nam accusantium perferendis laboriosam deserunt cum, voluptas nisi at totam veritatis nesciunt iste aspernatur nobis officiis laudantium dolore autem quo eum maiores."
        },
        {
          title: "Create Community Forum",
          pic: "Harari",
          due_date: "28 April 2020",
          status: "Ongoing",
          content:
            "Lorem ipsum dolor sit amet consectetur adipisicing elit. Nam accusantium perferendis laboriosam deserunt cum, voluptas nisi at totam veritatis nesciunt iste aspernatur nobis officiis laudantium dolore autem quo eum maiores."
        },
        {
          title: "Online Class with Zoom",
          pic: "Juleshwa",
          due_date: "26 April 2020",
          status: "Ongoing",
          content:
            "Lorem ipsum dolor sit amet consectetur adipisicing elit. Nam accusantium perferendis laboriosam deserunt cum, voluptas nisi at totam veritatis nesciunt iste aspernatur nobis officiis laudantium dolore autem quo eum maiores."
        }
      ]
    };
  },
  computed: {
    myProjects() {
      return this.projects.filter(project => {
        return project.pic === "Juleshwa";
      });
    }
  }
};
</script>
