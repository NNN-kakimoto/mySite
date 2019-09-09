<template>
  <v-list>
    <v-list-group
      no-action
      value="true"
      v-for="(year, key) in historys"
      :key="key"
      :value="(year.year == nowYear) ? true : false"
    >
      <template v-slot:activator>
        <v-list-item-content>
          <v-list-item-title>{{year.year}}</v-list-item-title>
        </v-list-item-content>
      </template>
      <v-divider></v-divider>
      <v-list-item
        v-for="(text, foo, idx) in year.data"
        :key="idx"
        tow-line
      >
        <v-list-item-content
          v-text="text"
          class="caption"
        />
      </v-list-item>
    </v-list-group>
  </v-list>
</template>
<script>
export default {
  props: [ 'historys' ],
  data () {
    return {
    }
  },
  created(){
    this.nowYear = new Date().getFullYear();
  }
}
</script>