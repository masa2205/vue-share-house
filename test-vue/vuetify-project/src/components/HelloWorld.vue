<template>
  <v-app>
    <v-navigation-drawer app v-model="drawer" clipped>
      <v-container>
        <v-list-item>
          <v-list-item-content>
            <v-list-item-title class="title blue--text text--darken-2">
              Navigation lists
            </v-list-item-title>
          </v-list-item-content>
        </v-list-item>
        <v-divider></v-divider>
        <v-list dense nav>
           <v-list-group 
            v-for="nav_list in nav_lists" 
            :key="nav_list.name" 
            :prepend-icon="nav_list.icon" 
            no-action 
            :append-icon="nav_list.lists ? undefined : ''"> 
              <template v-slot:activator>
                <v-list-item-content>
                  <v-list-item-title>{{ nav_list.name }}</v-list-item-title>
                </v-list-item-content>
              </template>
              <v-list-item v-for="list in nav_list.lists" :key="list">
                <v-list-item-content>
                  <v-list-item-title>{{ list }}</v-list-item-title>
                </v-list-item-content>
              </v-list-item>
           </v-list-group>
        </v-list>
      </v-container>
    </v-navigation-drawer>
    <v-app-bar color="info" dark app clipped-left>
      <v-app-bar-nav-icon @click="drawer=!drawer"></v-app-bar-nav-icon>
      <v-toolbar-title>Vuetify</v-toolbar-title>
      <v-spacer></v-spacer>
      <v-toolbar-items>
      <v-menu offset-y>
        <template v-slot:activator="{on}">
        <v-btn v-on="on" text elevation="24">Button<v-icon>mdi-menu-down</v-icon></v-btn>
        </template>
        <v-list>
          <v-list-item v-for="support in supports" :key="support.name">
           <v-list-item-icon>
           <v-icon>{{ support.icon }}</v-icon>
           </v-list-item-icon> 
           <v-list-item-content>
             <v-list-item-title>{{ support.name }}</v-list-item-title>
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
          {name:'HTML',icon:'mdi-vuetify'},
          {name:'CSS',icon:'mdi-discord'},
          {name:'JS',icon:'mdi-bug'},
          {name:'Python',icon:'mdi-github'},
          {name:'Vue.js',icon:'mdi-stack-overflow'},
        ],
        nav_lists:[
          {name: 'Getting Started',icon: 'mdi-vuetify',lists:['Quick Start','Pre-made layouts']},
          {name: 'Customization',icon: 'mdi-cogs'},
          {name: 'Styles & animations',icon: 'mdi-palette',lists:['Colors','Content','Display']},
          {name: 'UI Components',icon: 'mdi-view-dashboard',lists:['API explorer','Alerts']},
          {name: 'Directives',icon: 'mdi-function'},
          {name: 'Preminum themes',icon: 'mdi-vuetify'},
        ]
      }
   }
  } 
</script>