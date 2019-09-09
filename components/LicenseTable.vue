<template>
  <v-list flat>
    <v-list-item
      v-for="(item, index) in licenses"
      :key="index"
      class="outlined-list" 
    >
      <v-list-item-content v-text="item" />
    </v-list-item>
    
  </v-list>
</template>
<script>
export default {
  props: [ 'licenses' ]
}
</script>
<style lang="scss">
.outlined-list{
  box-sizing: content-box;
  border: 1px solid rgba(0, 0, 0, 0.12);
  border-bottom: none;
  &:hover{
    background-color: inherit;
  }
}
.v-list .outlined-list:last-child{
    border-bottom: 1px solid rgba(0, 0, 0, 0.12);
  }
</style>