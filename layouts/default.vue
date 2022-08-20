<template>
  <v-app>
    <common-header />

    <v-main>
      <v-container>
        <nuxt />
      </v-container>
    </v-main>

    <v-footer>
      &copy; {{ new Date().getFullYear() }} Amateur Radio Emergency Data
      Network, Inc.
    </v-footer>

    <common-loader />
    <common-error />
    <common-apimismatch />
    <settings-system />
  </v-app>
</template>

<script>
import { mapActions } from 'vuex'

export default {
  name: 'default',
  methods: {
    ...mapActions(['globalResources']),
  },
  created() {
    this.globalResources(['alerts', 'sysinfo'])
  },
}
</script>
