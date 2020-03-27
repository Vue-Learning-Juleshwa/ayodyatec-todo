<template>
  <div>
    <v-container class="my-5">
      <v-row wrap>
        <v-col cols="12" md="4" sd="6" lg="3" v-for="person in team" :key="person.name">
          <v-card text class="text-md-center ma-3 pa-2">
            <v-responsive class="pt-4">
              <v-avatar size="125" class="grey lighten-2 pa-3">
                <img :src="person.avatar" alt="Avatar Team" />
              </v-avatar>
            </v-responsive>
            <v-card-text>
              <div class="subtitle-1">{{person.name}}</div>
              <div class="grey--text">{{person.role}}</div>
            </v-card-text>
            <v-card-actions>
              <v-btn text color="orange">
                <v-icon small left>mdi-message</v-icon>
                <span>message</span>
              </v-btn>
            </v-card-actions>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
export default {
  name: "Team",
  data() {
    return {
      team: [
        {
          name: "Juleshwa",
          role: "Full Stack Developer",
          avatar: "https://image.flaticon.com/icons/svg/435/435039.svg"
        },
        {
          name: "Micha",
          role: "UI/UX Developer",
          avatar: "https://image.flaticon.com/icons/svg/435/435061.svg"
        },
        {
          name: "Bluebell",
          role: "Backend Engineer",
          avatar: "https://image.flaticon.com/icons/svg/145/145866.svg"
        },
        {
          name: "Harari",
          role: "Mobile Developer",
          avatar: "https://image.flaticon.com/icons/svg/435/435021.svg"
        }
      ]
    };
  }
};
</script>

<style>
</style>
