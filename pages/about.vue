<template>
  <div>
    <div class="py-10 px-5" v-html="about"></div>
    <h2 class="mt-5 px-5 headline">以下、大きめな更新履歴を載せます。</h2>
    <v-timeline
      dense
      class="pr-5 pb-5"
    >
      <v-timeline-item
        v-for="log in changelog"
        :key="log.date"
        fill-dot
        icon-color="accent"
        small
        class="pb-2"
      >
        <v-card class="elevation-2">
          <v-card-title class="headline" v-text="log.date" />
          <v-card-text v-text="log.comment" />
        </v-card>
      </v-timeline-item>
    </v-timeline>
  </div>
</template>

<script>
  import about from '~/src/static/about.md'
  import changelog from '~/src/changelog.json'

  export default {
    data() {
      return {
        changelog : changelog
      }
    },
    computed: {
      about() {
        return about
      }
    }
  }
</script>
<style lang="scss">
.hover-list-none:hover{
  background-color: inherit;
}
</style>