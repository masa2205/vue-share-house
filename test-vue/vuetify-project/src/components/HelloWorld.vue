<template>
  <v-app>
    <v-navigation-drawer app v-model="drawer" clipped>Navigation Lists</v-navigation-drawer>
    <v-app-bar color="info" dark app clipped-left>
      <v-app-bar-nav-icon @click="drawer=!drawer"></v-app-bar-nav-icon>
      <v-toolbar-title>Vuetify</v-toolbar-title>
      <v-spacer></v-spacer>
      <v-toolbar-items>
      <v-menu offset-y>
        <template v-slot:activator="{on}">
        <v-btn v-on="on" text elevation="24">Button</v-btn>
        </template>
        <v-list>
          <v-list-item v-for="support in supports" :key="support">
           <v-list-item-content>
             <v-list-item-title>{{ support }}</v-list-item-title>
           </v-list-item-content>
          </v-list-item>
        </v-list>
      </v-menu>
      </v-toolbar-items>
    </v-app-bar>
    <v-footer color="info" dark app>Vuetify</v-footer>
  </v-app>
</template>

<script>
  export default {
    data() {
      return{
        drawer: null,
        supports:[
          'HTML',
          'CSS',
          'JS',
          'Python',
          'Vue.js'
        ]
      }
   }
  } 
</script>