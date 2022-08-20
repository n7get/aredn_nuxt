<template>
  <v-card outlined height="100%">
    <v-card-title class="primary white--text">OLSR</v-card-title>

    <v-card-text class="pt-3">
      <v-row>
        <v-col cols="6">
          <span class="font-weight-bold">OLSR Entries:</span>
        </v-col>
        <v-col cols="6">
          {{ olsr.entries }}
        </v-col>

        <v-col cols="6">
          <span class="font-weight-bold">OLSR Nodes:</span>
        </v-col>
        <v-col cols="6">
          {{ olsr.nodes }}
        </v-col>
      </v-row>
    </v-card-text>
  </v-card>
</template>

<script>
import { mapGetters } from 'vuex'

export default {
  name: 'SystemInfo',
  computed: {
    ...mapGetters(['olsr']),
  },
}
</script>

