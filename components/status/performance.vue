<template>
  <v-card outlined height="100%">
    <v-card-title class="primary white--text">Performance</v-card-title>

    <v-card-text class="pt-3">
      <v-row>
        <v-col cols="6">
          <span class="font-weight-bold">Uptime:</span>
        </v-col>
        <v-col cols="6">
          {{ sysinfo.uptime }}
        </v-col>

        <v-col cols="6">
          <span class="font-weight-bold">Load (1m):</span>
        </v-col>
        <v-col cols="6">
          {{ sysinfo && sysinfo.loads ? sysinfo.loads[0] : 'N/A' }}
        </v-col>

        <v-col cols="6">
          <span class="font-weight-bold">Load (5m):</span>
        </v-col>
        <v-col cols="6">
          {{ sysinfo && sysinfo.loads ? sysinfo.loads[1] : 'N/A' }}
        </v-col>

        <v-col cols="6">
          <span class="font-weight-bold">Load (15m):</span>
        </v-col>
        <v-col cols="6">
          {{ sysinfo && sysinfo.loads ? sysinfo.loads[2] : 'N/A' }}
        </v-col>
      </v-row>
    </v-card-text>
  </v-card>
</template>

<script>
import { mapGetters } from 'vuex'
import systeminfoVue from './systeminfo.vue'

export default {
  name: 'Performance',
  computed: {
    ...mapGetters(['sysinfo']),
  },
}
</script>
