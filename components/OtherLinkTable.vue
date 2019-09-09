<template>
  <div>
    <v-card
      v-for="(item, index) in links"
      :key="index"
      flat
      :href="item.path"
      target="_blank"
      class="hover-card"
    >
      <v-card-title  class="body-1 pb-0">
        <span v-text="item.name"></span><v-icon>mdi-chevron-double-right</v-icon>
      </v-card-title>
      <v-divider />
      <v-card-text v-html="item.comment.replace(/\r?\n/g, '<br>')" class="pt-0" />
    </v-card>
    
  </div>
</template>
<script>
export default {
  props: [ 'links' ]
}
</script>
<style lang="scss">
.hover-card:hover{
  background-color: rgba(0, 0, 0, 0.05);
}
</style>