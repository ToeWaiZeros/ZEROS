<template>
    <v-app id="inspire">
      <v-navigation-drawer
        v-model="drawer"
        fixed
        app
      >
      <v-list>
          <v-list-group
            v-for="item in items"
            v-model="item.active"
            :key="item.title"
            :prepend-icon="item.action"
            no-action
          >
            <v-list-tile slot="activator">
              <v-list-tile-content>
                <v-list-tile-title>{{ item.title }}</v-list-tile-title>
              </v-list-tile-content>
            </v-list-tile>

            <v-list-tile
              v-for="subItem in item.items"
              :key="subItem.title"
              @click=""
            >
              <v-list-tile-content>
                <v-list-tile-title>{{ subItem.title }}</v-list-tile-title>
              </v-list-tile-content>

              <v-list-tile-action>
                <v-icon>{{ subItem.action }}</v-icon>
              </v-list-tile-action>
            </v-list-tile>
          </v-list-group>
        </v-list>
      </v-navigation-drawer>
      <v-toolbar color="indigo" dark fixed app>
        <v-toolbar-side-icon @click.stop="drawer = !drawer"></v-toolbar-side-icon>
        <v-toolbar-title>Application</v-toolbar-title>
      </v-toolbar>
      <v-content>
        <v-container fluid fill-height>
          <v-layout
            justify-center
            align-center
          >
            <v-flex text-xs-center>
              <v-tooltip left>
                <v-btn slot="activator" :href="source" icon large target="_blank">
                  <v-icon large>code</v-icon>
                </v-btn>
                <span>Source</span>
              </v-tooltip>
              <v-tooltip right>
                <v-btn slot="activator" icon large href="https://codepen.io/johnjleider/pen/rJdVMq" target="_blank">
                  <v-icon large>mdi-codepen</v-icon>
                </v-btn>
                <span>Codepen</span>
              </v-tooltip>
            </v-flex>
          </v-layout>
        </v-container>
      </v-content>
      <v-footer color="indigo" app>
        <span class="white--text">&copy; 2017</span>
      </v-footer>
    </v-app>
  </template>
  
  <script>
    export default {
      data: () => ({
        drawer: null,
        items: [
          {
            action: 'person',
            title: 'Supplier',
            // items: [
            //   {action:'person_add', title: 'New Spplier' },
            // ]
          }, 
          {
            action: 'people',
            title: 'Customer',
            // items: [
            //   { 
            //     action:'group_add',
            //     title: 'New Customer' }
            // ]
          }
        ]
      }),
      props: {
        source: String,
      }
    }
  </script>