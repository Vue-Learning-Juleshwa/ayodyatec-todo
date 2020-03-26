<template>
  <v-app>
    <Navbar />
    <v-content class="mx-4 my-4">
      <router-view />
    </v-content>
  </v-app>
</template>

<script>
  import Navbar from '@/components/Navbar';
  export default {
    name: 'App',

    components: {
      Navbar
    },

    data: () => ({
      //
    })
  };
</script>

<style>
  #app {
    background: rgb(204, 204, 204);
  }
</style>
