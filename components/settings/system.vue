<template>
  <v-dialog v-model="showDialog" max-width="400">
    <v-card>
      <v-card-title>
        <h2>System settings</h2>
      </v-card-title>
      <v-card-text></v-card-text>
      <v-card-actions>
        <v-spacer />
        <v-btn small right class="warning" @click="save">Save</v-btn>
        <v-btn small right class="error" @click="cancel">Cancel</v-btn>
      </v-card-actions>
    </v-card>
  </v-dialog>
</template>

<script>
import { mapActions, mapGetters } from 'vuex'

export default {
  name: 'system-settings',
  data() {
    return {
      showDialog: false,
    }
  },
  methods: {
    ...mapActions(['clearApiMismatch']),
    cancel() {
      this.showDialog = false
    },
    save() {
      this.showDialog = false
    },
  },
  computed: {
    ...mapGetters(['hasApiMismatch', 'nodeName', 'legacyUrl']),
  },
  created() {
    this.$nuxt.$on('show-system-setup', () => {
      this.showDialog = true
    })
  },
}
</script>
