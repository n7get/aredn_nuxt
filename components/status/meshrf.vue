<template>
  <v-card outlined height="100%">
    <v-card-title class="primary">
      <v-row>
        <v-col cols="10" class="white--text">Mesh RF</v-col>
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
          <span class="font-weight-bold">SSID:</span>
        </v-col>
        <v-col cols="6">
          {{ meshrf.ssid === undefined ? 'Disabled' : meshrf.ssid }}
        </v-col>

        <v-col cols="6">
          <span class="font-weight-bold">Channel:</span>
        </v-col>
        <v-col cols="6">
          {{ meshrf.channel === undefined ? 'Disabled' : meshrf.channel }}
        </v-col>

        <v-col cols="6">
          <span class="font-weight-bold">Bandwidth (MHz):</span>
        </v-col>
        <v-col cols="6">
          {{ meshrf.chanbw === undefined ? 'Disabled' : meshrf.chanbw }}
        </v-col>

        <v-col cols="6">
          <span class="font-weight-bold">Frequency (MHz):</span>
        </v-col>
        <v-col cols="6">
          {{ meshrf.frequency === undefined ? 'Disabled' : meshrf.frequency }}
        </v-col>
      </v-row>
    </v-card-text>
  </v-card>
</template>

<script>
import { mapGetters } from 'vuex'

export default {
  name: 'MeshRF',
  methods: {
    openSettings() {
      $nuxt.$emit('show-mesh-setup')
    },
  },
  computed: {
    ...mapGetters(['meshrf']),
  },
}
</script>
