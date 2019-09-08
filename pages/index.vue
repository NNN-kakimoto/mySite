<template>
  <v-layout
    column
    justify-center
    align-center
  >
    <v-flex
      xs12
      sm8
      md6
    >
    </v-flex>
  </v-layout>
</template>

<script>

export default {
  components: {
    Logo,
    VuetifyLogo
  },
  asyncData() {
    return {
      profile: require(`~/src/profile.json`)
    }
  }
}
</script>
