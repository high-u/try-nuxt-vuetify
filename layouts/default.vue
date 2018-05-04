<template>
  <div id="app">
    <v-app id="inspire">
      <v-navigation-drawer fixed v-model="drawerRight" right clipped app>
        <v-toolbar flat>
          <v-list>
            <v-list-tile>
              <v-list-tile avatar>
                <v-list-tile-avatar>
                  <v-icon medium>account_circle</v-icon>
                </v-list-tile-avatar>
                <v-list-tile-content>
                  <v-list-tile-title class="title">
                    User
                  </v-list-tile-title>
                </v-list-tile-content>
              </v-list-tile>
            </v-list-tile>
          </v-list>
        </v-toolbar>
        <v-list dense>
          <v-list-tile @click.stop="right = !right">
            <v-list-tile-action>
              <v-icon>exit_to_app</v-icon>
            </v-list-tile-action>
            <v-list-tile-content>
              <v-list-tile-title>Open Temporary Drawer</v-list-tile-title>
            </v-list-tile-content>
          </v-list-tile>
        </v-list>
        <v-list dense class="pt-0">
        <v-list-tile v-for="item in items" :key="item.title" :to="item.url">
          <v-list-tile-action>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-tile-action>
          <v-list-tile-content>
            <v-list-tile-title>{{ item.title }}</v-list-tile-title>
          </v-list-tile-content>
        </v-list-tile>
      </v-list>
      </v-navigation-drawer>
      <v-toolbar color="blue-grey darken-2" dark fixed app clipped-right>
        <v-toolbar-side-icon @click.stop="drawer = !drawer"></v-toolbar-side-icon>
        <v-toolbar-title>Toolbar</v-toolbar-title>
        <v-spacer></v-spacer>
        <v-toolbar-items class="hidden-sm-and-down">
          <v-btn flat v-for="item in items" :key="item.title" :to="item.url">
            {{ item.title }}
          </v-btn>
        </v-toolbar-items>
        <v-toolbar-side-icon @click.stop="drawerRight = !drawerRight"></v-toolbar-side-icon>
      </v-toolbar>
      <v-navigation-drawer fixed v-model="drawer" app>
        <v-toolbar flat>
          <v-list>
            <v-list-tile>
              <v-list-tile avatar>
                <v-list-tile-avatar>
                  <v-icon medium>account_circle</v-icon>
                </v-list-tile-avatar>
                <v-list-tile-content>
                  <v-list-tile-title class="title">
                    User
                  </v-list-tile-title>
                </v-list-tile-content>
              </v-list-tile>
            </v-list-tile>
          </v-list>
        </v-toolbar>
        <v-list dense>
          <v-list-tile @click.stop="left = !left">
            <v-list-tile-action>
              <v-icon>exit_to_app</v-icon>
            </v-list-tile-action>
            <v-list-tile-content>
              <v-list-tile-title>Open Temporary Drawer</v-list-tile-title>
            </v-list-tile-content>
          </v-list-tile>
        </v-list>
        <v-list dense class="pt-0">
        <v-list-tile v-for="item in items" :key="item.title" :to="item.url">
          <v-list-tile-action>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-tile-action>
          <v-list-tile-content>
            <v-list-tile-title>{{ item.title }}</v-list-tile-title>
          </v-list-tile-content>
        </v-list-tile>
      </v-list>
      </v-navigation-drawer>
      <v-navigation-drawer temporary v-model="left" fixed>
        Left
      </v-navigation-drawer>
      <v-content>
        <v-container fluid fill-height>
          <v-layout justify-center align-center>
            <v-flex text-xs-center>
            <div>
              <nuxt/>
            </div>
          </v-flex>
          </v-layout>
        </v-container>
      </v-content>
      <v-navigation-drawer right temporary v-model="right" fixed>
        Right
      </v-navigation-drawer>
      <v-footer color="blue-grey darken-2" app class="white--text">
      &copy;2018 — <strong>Vuetify</strong>
      <v-spacer></v-spacer>
      <v-btn v-for="icon in icons" :key="icon" icon class="white--text">
        <v-icon small>{{ icon }}</v-icon>
      </v-btn>
    </v-footer>
    </v-app>
  </div>
</template>

<script>
import MyFooter from '~/components/Footer.vue'
import feature from '~/pages/feature.vue'
import contact from '~/pages/contact.vue'

export default {
  components: {
    MyFooter,
    feature,
    contact
  },
  data: () => ({
    drawer: null,
    items: [
      { title: 'Home', icon: 'home', url: '/' },
      { title: 'Feature', icon: 'code', url: '/feature' },
      { title: 'Contact', icon: 'question_answer', url: '/contact' }
    ],
    icons: ['fa-facebook', 'fa-twitter', 'fa-google-plus', 'fa-linkedin', 'fa-instagram'],
    // drawer: true,
    drawerRight: true,
    right: null,
    left: null
  }),
  props: {
    source: String
  }
}
</script>
