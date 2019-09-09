<template>
  <v-layout
    column
    justify-center
    align-center
    class="sticky-parent"
  >
    <v-img
      :src="require('~/assets/images/top-bg.JPG')"
      class="sticky-image"
      gradient="to top right, rgba(100,115,201,.23), rgba(25,32,72,.7)"
    />
    <v-row
      class="display-text pa-10"
    >
      <v-flex
        xs12
        sm6
        md6
        class="px-2"
      >
        <div
          class="display-1 text-center article-title"
        >How About?</div>
      </v-flex>
      <v-flex
        xs12
        sm6
      >
        <p class="mb-0">履歴書代わりになったらいいな、と密かに目論んで作成したページです。</p><n-link to="/about">くわしく</n-link>
      </v-flex>
    </v-row>

    <v-img
      :src="require('~/assets/images/middle-bg.JPG')"
      class="sticky-image"
      gradient="to top right, rgba(100,115,201,.23), rgba(25,32,72,.7)"
    />

    <v-row
      class="display-text pa-10"
    >
      <v-flex
        xs12
        sm6
        md6
        class="px-2 text-center"
      >
        <div
          class="display-1 article-title align-self-center"
        >History</div>
        <p class="subtitle-1">略歴・職歴(2016〜)</p>
      </v-flex>
      <v-flex
        xs12
        sm6
      >
        <history-table :historys="profile.history" />
      </v-flex>
    </v-row>
    <v-row
      class="display-text pa-10 display reverse"
    >
      <v-flex
        xs12
        sm6
        md6
        class="px-2 text-center"
      >
        <div
          class="display-1 article-title align-self-center"
        >License</div>
        <p class="subtitle-1">これまでに取得した資格です。</p>
      </v-flex>
      <v-flex
        xs12
        sm6
      >
        <lisence-table :licenses="profile.licenses" />
      </v-flex>
    </v-row>

    <v-img
      :src="require('~/assets/images/bottom-bg.JPG')"
      class="sticky-image"
      gradient="to top right, rgba(100,115,201,.23), rgba(25,32,72,.7)"
    />

    <v-row
      class="display-text pa-10"
    >
      <v-flex
        xs12
        sm6
        md6
        class="px-2 text-center"
      >
        <div
          class="display-1 article-title align-self-center"
        >Service</div>
        <p class="subtitle-1">これまでに公開したサービスです。</p>
      </v-flex>
      <v-flex
        xs12
        sm6
      >
        <other-link-table :links="profile.services" />
      </v-flex>
    </v-row>
    <v-row
      class="display-text pa-10 display reverse"
    >
      <v-flex
        xs12
        sm6
        md6
        class="px-2 text-center"
      >
        <div
          class="display-1 article-title align-self-center"
        >Media</div>
        <p class="subtitle-1">これまでに掲載されたメディアです。</p>
      </v-flex>
      <v-flex
        xs12
        sm6
      >
        <other-link-table :links="profile.medias" />
      </v-flex>
    </v-row>
  </v-layout>
</template>

<script>
import profile from '~/src/profile.json'

import HistoryTable from '@/components/HistoryTable'
import LisenceTable from '@/components/LicenseTable'
import OtherLinkTable from '@/components/OtherLinkTable'
export default {
  components: {
    HistoryTable,
    LisenceTable,
    OtherLinkTable
  },
  data () {
    return {
      profile : profile
    }
  }
}
</script>
<style lang="scss">
.sticky-parent{
  position: relative;
}
.sticky-image{
  position: sticky;
  top: 0px;
  max-width: 100vw;

}
.display-text{
  z-index: 100;
  width: 100vw;
  background-color: white;

  .article-title{
    border-bottom: #9e3838cb 3px solid;
  }
}
.reverse{
  flex-direction: row-reverse;
}
</style>
