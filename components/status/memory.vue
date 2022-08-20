<template>
  <v-card outlined height="100%">
    <v-card-title class="primary white--text">Memory</v-card-title>

    <v-card-text class="pt-3">
      <v-row>
        <v-col cols="6">
          <span class="font-weight-bold">Total RAM:</span>
        </v-col>
        <v-col cols="6"> {{ memory.totalram }} KB </v-col>

        <v-col cols="6">
          <span class="font-weight-bold">Free RAM:</span>
        </v-col>
        <v-col cols="6">
          {{ memory.freeram }} KB
          <v-progress-linear v-model="freerampctfree" />
        </v-col>

        <v-col cols="6">
          <span class="font-weight-bold">Shared RAM:</span>
        </v-col>
        <v-col cols="6"> {{ memory.sharedram }} KB </v-col>

        <v-col cols="6">
          <span class="font-weight-bold">Buffer RAM:</span>
        </v-col>
        <v-col cols="6"> {{ memory.bufferram }} KB </v-col>
      </v-row>
    </v-card-text>
  </v-card>
</template>

<script>
import { mapGetters } from 'vuex'

export default {
  name: 'FilesystemInfo',
  computed: {
    ...mapGetters(['memory']),
    freerampctfree() {
      return ((this.memory.freeram / this.memory.totalram) * 100).toFixed(3)
    },
  },
}
</script>
