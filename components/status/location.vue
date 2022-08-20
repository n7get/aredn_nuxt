<template>
  <v-card outlined height="100%">
    <v-card-title class="primary">
      <v-row>
        <v-col cols="10" class="white--text">Location</v-col>
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
          <span class="font-weight-bold">Latitude:</span>
        </v-col>
        <v-col cols="6">
          {{ location.lat === '' ? 'Not set' : location.lat }}
        </v-col>

        <v-col cols="6">
          <span class="font-weight-bold">Longitude:</span>
        </v-col>
        <v-col cols="6">
          {{ location.lon === '' ? 'Not set' : location.lon }}
        </v-col>

        <v-col cols="6">
          <span class="font-weight-bold">Grid Square:</span>
        </v-col>
        <v-col cols="6">
          {{ location.gridsquare === '' ? 'Not set' : location.gridsquare }}
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
      $nuxt.$emit('show-location-setup')
    },
  },
  computed: {
    ...mapGetters(['location']),
  },
}
</script>
