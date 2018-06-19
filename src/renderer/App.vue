<template>
  <div id="app">
    <v-app dark>
      <v-navigation-drawer v-model="drawer" clipped floating app>
        <v-list>
          <v-list-tile 
            router 
            :to="item.to"
            :key="i"
            v-for="(item, i) in items"
            exact
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
      <v-toolbar app clipped-left>
        <v-toolbar-side-icon @click.native.stop="drawer = !drawer"></v-toolbar-side-icon>
        <v-toolbar-title v-text="title"></v-toolbar-title>
        <v-spacer></v-spacer>
        <v-btn flat>
          <v-icon left>lock_open</v-icon>
          Login
        </v-btn>
      </v-toolbar>
      <v-content>
        <v-container fluid fill-height>
          <v-slide-y-transition mode="out-in">
            <router-view></router-view>
          </v-slide-y-transition>
        </v-container>
      </v-content>

      <v-footer app>
        <v-spacer></v-spacer>
        <span>&copy; 2017</span>
      </v-footer>
    </v-app>
  </div>
</template>

<script>
  export default {
    name: 'support-admin',
    data: () => ({
      drawer: false,
      items: [
        { icon: 'category', title: 'Platform', to: '/platform' },
        { icon: 'timeline', title: 'Metrics', to: '/metrics' },
        { icon: 'lock_open', title: 'Login', to: '/user/login' }
      ],
      title: 'Support Control Panel'
    })
  }
</script>

<style>
  @import url('https://fonts.googleapis.com/css?family=Roboto:300,400,500,700|Material+Icons');
  /* Global CSS */
</style>
