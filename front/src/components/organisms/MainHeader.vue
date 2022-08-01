<template>
  <!--
  <v-app-bar flat app dark color="parimary">
    <div>unko</div>
    <v-spacer />
    <div>unko2</div>
  </v-app-bar>
-->
  <v-app-bar color="primary" dark app>
    <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>
    <v-toolbar-title>Vuetify</v-toolbar-title>
    <v-text-field value="unkooo" />
    <unko value="test" />
  </v-app-bar>
</template>

<script>
export default {}
</script>
