<template>
  <nav>
    <v-snackbar v-model="snackbar" top color="teal" :timeout="4000">
      <span>Awesome! You add new project!</span>
      <v-btn text color="white" @click="snackbar = false">Close</v-btn>
    </v-snackbar>

    <v-app-bar app>
      <v-app-bar-nav-icon class="grey--text" @click="drawer = !drawer"></v-app-bar-nav-icon>
      <v-toolbar-title class="text-uppercase grey--text">
        <span class="font-weight-light">AyodyaTec</span>
        <span class="font-weight-bold">Todo</span>
      </v-toolbar-title>
      <v-spacer></v-spacer>

      <!-- Drop Down Menu -->

      <v-menu>
        <template v-slot:activator="{ on }">
          <v-btn text class="grey" dark v-on="on">
            <v-icon>mdi-chevron-down</v-icon>
            <span>menu</span>
          </v-btn>
        </template>
        <v-list>
          <v-list-item v-for="link in links" :key="link.title" :to="link.path">
            <v-list-item-title>{{link.title}}</v-list-item-title>
          </v-list-item>
        </v-list>
      </v-menu>

      <v-btn text color="grey">
        <span>Logout</span>
        <v-icon right>mdi-exit-to-app</v-icon>
      </v-btn>
    </v-app-bar>

    <!-- Navigation Drawer -->
    <v-navigation-drawer app v-model="drawer" color="info">
      <v-row class="text-center">
        <v-col class="mt-5">
          <v-avatar size="75">
            <img src="https://image.flaticon.com/icons/svg/435/435039.svg" alt="Avatar Account" />
          </v-avatar>
          <p class="white--text subheading-1">Juleshwa</p>
        </v-col>
        <v-col>
          <Popup @projectAdded="snackbar = true" />
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
import Popup from "./Popup";
export default {
  name: "Navbar",
  data() {
    return {
      drawer: false,
      links: [
        { title: "Dashboard", icon: "mdi-view-dashboard", path: "/" },
        { title: "My Projects", icon: "mdi-folder", path: "/projects" },
        { title: "Team", icon: "mdi-account", path: "/team" }
      ],
      snackbar: false
    };
  },
  components: {
    Popup
  }
};
</script>

<style scoped></style>
