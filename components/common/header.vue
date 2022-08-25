<template>
  <div>
    <v-app-bar :clipped-left="clipped" flat fixed app>
      <v-app-bar-nav-icon @click.stop="drawer = !drawer" />
      <v-app-bar-title v-text="nodeName" />
      <v-spacer />
      <v-col cols="4" sm="2" align="right">
        <v-icon v-show="hasSeenAlerts" @click="clearSeenAlerts" class="mr-2">
          mdi-alert-circle
        </v-icon>
        <v-icon @click="emitRefresh">mdi-refresh</v-icon>
      </v-col>
      <!-- <template v-slot:extension>
        <div class="hidden-xs-only">
          <v-btn small plain to="/" router exact nuxt>Status</v-btn>
          <v-btn small plain>Nodes</v-btn>
          <v-btn small plain>Networking</v-btn>
          <v-btn small plain>Services</v-btn>
          <v-btn small plain to="/" router exact nuxt>Tuning</v-btn>
          <v-btn small plain>Tunnel</v-btn>
          <v-btn small plain>System</v-btn>
        </div>
      </template> -->
    </v-app-bar>

    <v-navigation-drawer
      v-model="drawer"
      :mini-variant="miniVariant"
      clipped
      app
    >
      <v-list flat>
        <v-list-item to="/" router exact nuxt>
          <v-list-item-content>
            <v-list-item-title>Status</v-list-item-title>
          </v-list-item-content>
        </v-list-item>

        <v-list-group>
          <template v-slot:activator>
            <v-list-item-title>Nodes</v-list-item-title>
          </template>
          <v-list-item to="/" router exact nuxt>
            <v-list-item-content class="ml-4">
              <v-list-item-title>Neighbors</v-list-item-title>
            </v-list-item-content>
          </v-list-item>
          <v-list-item to="/" router exact nuxt>
            <v-list-item-content class="ml-4">
              <v-list-item-title>Favorites</v-list-item-title>
            </v-list-item-content>
          </v-list-item>
          <v-list-item to="/" router exact nuxt>
            <v-list-item-content class="ml-4">
              <v-list-item-title>All Noddes</v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </v-list-group>

        <v-list-group>
          <template v-slot:activator>
            <v-list-item-title>Networking</v-list-item-title>
          </template>
          <v-list-item to="/" router exact nuxt>
            <v-list-item-content class="ml-4">
              <v-list-item-title>Mesh</v-list-item-title>
            </v-list-item-content>
          </v-list-item>
          <v-list-item to="/" router exact nuxt>
            <v-list-item-content class="ml-4">
              <v-list-item-title>LAN</v-list-item-title>
            </v-list-item-content>
          </v-list-item>
          <v-list-item to="/" router exact nuxt>
            <v-list-item-content class="ml-4">
              <v-list-item-title>WAN</v-list-item-title>
            </v-list-item-content>
          </v-list-item>
          <v-list-item to="/" router exact nuxt>
            <v-list-item-content class="ml-4">
              <v-list-item-title>WiFi Scan</v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </v-list-group>

        <v-list-item to="/" router exact nuxt>
          <v-list-item-content>
            <v-list-item-title>Services</v-list-item-title>
          </v-list-item-content>
        </v-list-item>

        <v-list-group>
          <template v-slot:activator>
            <v-list-item-title>Services</v-list-item-title>
          </template>
          <v-list-item to="/" router exact nuxt>
            <v-list-item-content class="ml-4">
              <v-list-item-title>My Services</v-list-item-title>
            </v-list-item-content>
          </v-list-item>
          <v-list-item to="/" router exact nuxt>
            <v-list-item-content class="ml-4">
              <v-list-item-title>Favorites</v-list-item-title>
            </v-list-item-content>
          </v-list-item>
          <v-list-item to="/" router exact nuxt>
            <v-list-item-content class="ml-4">
              <v-list-item-title>All Services</v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </v-list-group>

        <v-list-item to="/" router exact nuxt>
          <v-list-item-content>
            <v-list-item-title>Tuning</v-list-item-title>
          </v-list-item-content>
        </v-list-item>

        <v-list-group>
          <template v-slot:activator>
            <v-list-item-title>System</v-list-item-title>
          </template>
          <v-list-item to="/" router exact nuxt>
            <v-list-item-content class="ml-4">
              <v-list-item-title>General</v-list-item-title>
            </v-list-item-content>
          </v-list-item>
          <v-list-item to="/" router exact nuxt>
            <v-list-item-content class="ml-4">
              <v-list-item-title>Firmware Update</v-list-item-title>
            </v-list-item-content>
          </v-list-item>
          <v-list-item to="/" router exact nuxt>
            <v-list-item-content class="ml-4">
              <v-list-item-title>Package Management</v-list-item-title>
            </v-list-item-content>
          </v-list-item>
          <v-list-item to="/" router exact nuxt>
            <v-list-item-content class="ml-4">
              <v-list-item-title>SSH Keys</v-list-item-title>
            </v-list-item-content>
          </v-list-item>
          <v-list-item to="/" router exact nuxt>
            <v-list-item-content class="ml-4">
              <v-list-item-title>Time</v-list-item-title>
            </v-list-item-content>
          </v-list-item>
          <v-list-item to="/" router exact nuxt>
            <v-list-item-content class="ml-4">
              <v-list-item-title>Advanced Configuration</v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </v-list-group>
      </v-list>
    </v-navigation-drawer>
  </div>
</template>

<script>
import { mapActions, mapGetters } from 'vuex'

export default {
  data() {
    return {
      clipped: true,
      drawer: false,
      miniVariant: false,
    }
  },
  methods: {
    ...mapActions(['clearSeenAlerts']),
    emitRefresh() {
      $nuxt.$emit('refresh-node')
    },
  },
  computed: {
    ...mapGetters(['seenAlerts', 'nodeName']),
    hasSeenAlerts() {
      return !!this.seenAlerts.aredn || !!this.seenAlerts.local
    },
  },
}
</script>
