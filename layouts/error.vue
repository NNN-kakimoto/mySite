<template>
  <v-app dark class="pa-10">
    <h1 class="display-4" v-if="error.statusCode === 404">
      {{ pageNotFound }}
    </h1>
    <h1 v-else>
      {{ otherError }}
    </h1>
    <v-container>
      <v-row>
        <v-col>
          <v-img :src="require('~/assets/images/gomennasai.gif')" :aspect-ratio="9/16"/>
        </v-col>
        <v-col>
          <h2>「なにもしてないのに壊れました」な状態のときは<a href="https://www.twitter.com/kakimoto_itc" target="_blank"><v-icon color="#1976d2">mdi-twitter</v-icon>twitter</a>まで連絡してみてください。(改善するとは限りません。)</h2>
          <NuxtLink to="/">
            トップへはこちら
          </NuxtLink>
        </v-col>
      </v-row>
    </v-container>
  </v-app>
</template>

<script>
export default {
  layout: 'empty',
  props: {
    error: {
      type: Object,
      default: null
    }
  },
  head () {
    const title =
      this.error.statusCode === 404 ? this.pageNotFound : this.otherError
    return {
      title
    }
  },
  data () {
    return {
      pageNotFound: '404 Not Found',
      otherError: 'An error occurred'
    }
  }
}
</script>

<style scoped>
h1 {
  font-size: 20px;
}
</style>
