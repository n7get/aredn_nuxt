<template>
  <v-card outlined height="100%">
    <v-card-title class="primary white--text">Filesystem</v-card-title>

    <v-card-text class="pt-3">
      <v-row>
        <v-col cols="6">
          <span class="font-weight-bold">Total space in /:</span>
        </v-col>
        <v-col cols="6">
          {{ storage.roottotal }} KB
        </v-col>

        <v-col cols="6">
          <span class="font-weight-bold">Freespace in /:</span>
        </v-col>
        <v-col cols="6">
          {{ storage.rootfree }} KB
          <v-progress-linear v-model="rootpctfree" />
        </v-col>

        <v-col cols="6">
          <span class="font-weight-bold">Total space in /tmp:</span>
        </v-col>
        <v-col cols="6">
          {{ storage.tmptotal }} KB
        </v-col>

        <v-col cols="6">
          <span class="font-weight-bold">Freespace in /tmp:</span>
        </v-col>
        <v-col cols="6">
          {{ storage.tmpfree }} KB
          <v-progress-linear v-model="tmppctfree" />
        </v-col>
      </v-row>
    </v-card-text>
  </v-card>
</template>

<script>
import { mapGetters } from 'vuex'

export default {
  name: 'FilesystemInfo',
  computed: {
    ...mapGetters(['storage']),
    rootpctfree() {
      return ((this.storage.rootfree / this.storage.roottotal) * 100).toFixed(3)
    },
    tmppctfree() {
      return ((this.storage.tmpfree / this.storage.tmptotal) * 100).toFixed(3)
    },
  },
}
</script>
