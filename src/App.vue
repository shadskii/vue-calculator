<template>
  <v-app :dark="dark">
    <v-navigation-drawer
      persistent
      :mini-variant="miniVariant"
      :clipped="clipped"
      v-model="drawer"
      enable-resize-watcher
      fixed
      app
    >
      <v-list>
        <v-list-tile
          value="true"
          v-for="(item, i) in items"
          :key="i"
        >
          <v-list-tile-action>
            <v-icon v-html="item.icon"></v-icon>
          </v-list-tile-action>
          <v-list-tile-content>
            <v-list-tile-title v-text="item.title"></v-list-tile-title>
          </v-list-tile-content>
        </v-list-tile>
      </v-list>
    </v-navigation-drawer>
    <v-toolbar
      app
      :clipped-left="clipped"
    >
      <v-toolbar-side-icon @click.stop="drawer = !drawer"></v-toolbar-side-icon>
      <v-toolbar-title v-text="title"></v-toolbar-title>
      <v-spacer></v-spacer>
      <v-toolbar-items class="hidden-sm-and-down">
        <v-switch
          :label="dark ? 'light':'dark'"
          v-model="dark"
        ></v-switch>
      </v-toolbar-items>
    </v-toolbar>
    <v-content>
      <main-layout/>
    </v-content>
   
    <v-footer :fixed="fixed" app>
      <span>&copy; 2017</span>
    </v-footer>
  </v-app>
</template>

<script>
import MainLayout from "./components/MainLayout";
export default {
  name: "App",
  components: {
    MainLayout
  },
  data() {
    return {
      clipped: false,
      drawer: false,
      fixed: false,
      dark: false,
      items: [
        {
          icon: "bubble_chart",
          title: "Yupp"
        }
      ],
      miniVariant: false,
      title: "Vuetify.js"
    };
  }
};
</script>
