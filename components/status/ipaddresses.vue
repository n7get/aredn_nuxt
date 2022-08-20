<template>
  <v-card outlined height="100%">
    <v-card-title class="primary">
      <v-row>
        <v-col cols="10" class="white--text">IP Addresses</v-col>
        <v-col cols="2" align="right">
          <v-icon @click.stop="openSettings" class="white--text">
            mdi-cog
          </v-icon>
        </v-col>
      </v-row>
    </v-card-title>

    <v-card-text class="pt-3">
      <v-row>
        <v-col cols="6">
          <span class="font-weight-bold">RF:</span>
        </v-col>
        <v-col cols="6">
          {{ ip.wifi === '' ? 'Disabled' : ip.wifi }}
        </v-col>

        <v-col cols="6">
          <span class="font-weight-bold">LAN:</span>
        </v-col>
        <v-col cols="6">
          {{ ip.lan }}
        </v-col>

        <v-col cols="6">
          <span class="font-weight-bold">WAN:</span>
        </v-col>
        <v-col cols="6">
          {{ ip.wan === '' ? 'n/a' : ip.wan }}
        </v-col>

        <v-col cols="6">
          <span class="font-weight-bold">Gateway:</span>
        </v-col>
        <v-col cols="6">
          {{ ip.gateway }}
        </v-col>
      </v-row>
    </v-card-text>
  </v-card>
</template>

<script>
import { mapGetters } from 'vuex'

export default {
  name: 'IPAddresses',
  methods: {
    openSettings() {
      $nuxt.$emit('show-ipaddresses-setup')
    },
  },
  computed: {
    ...mapGetters(['ip']),
  },
}
</script>
