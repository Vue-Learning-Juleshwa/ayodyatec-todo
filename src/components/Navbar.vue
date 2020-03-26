<template>
  <nav>
    <v-app-bar flat app>
      <v-app-bar-nav-icon class="grey--text" @click="drawer = !drawer"></v-app-bar-nav-icon>
      <v-app-bar-title class="text-uppercase grey--text">
        <span class="font-weight-light">Vuetify</span>
        <span class="font-weight-bold">Todo</span>
      </v-app-bar-title>
      <v-spacer></v-spacer>
      <v-btn text color="grey">
        <span>Logout</span>
        <v-icon right>mdi-exit-to-app</v-icon>
      </v-btn>
    </v-app-bar>
    <v-navigation-drawer app v-model="drawer" color="info">
      <v-row class="text-center">
        <v-col class="mt-5">
          <v-avatar size="75">
            <img src="https://image.flaticon.com/icons/svg/435/435039.svg" alt="Avatar Account" />
          </v-avatar>
          <p class="white--text subheading-1 mt-3">Juleshwa</p>
        </v-col>
      </v-row>
      <v-list>
        <v-list-item v-for="link in links" :key="link.title" :to="link.path">
          <v-list-item-action>
            <v-icon class="white--text">{{ link.icon }}</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title class="white--text">
              {{
              link.title
              }}
            </v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
  </nav>
</template>

<script>
export default {
  name: "Navbar",
  data() {
    return {
      drawer: false,
      links: [
        { title: "Dashboard", icon: "mdi-view-dashboard", path: "/" },
        { title: "My Projects", icon: "mdi-folder", path: "/projects" },
        { title: "Team", icon: "mdi-account", path: "/team" }
      ]
    };
  }
};
</script>

<style scoped></style>
