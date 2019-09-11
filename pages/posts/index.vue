<template>
  <div class="py-10 px-5">
    <h2 class="mb-5 px-5 headline">記事一覧</h2>
    <v-card
      flat
      v-for="post in displayPosts"
      :key="post.id"
      :to="'/posts/'+post.path"
      class="pa-5 hover-gray"
    >
      <v-card-title v-text="post.title"
        class="pa-0"
      />
      <v-divider></v-divider>
      <v-card-text
        v-text="post.date"
        class="subtitle-2 pa-0"
      />
      <v-card-text
        v-text="post.beginning"
        class="overflow-triple-reader pa-0"
      />
    </v-card>
    <v-pagination
      v-model="nowPage"
      :length="pagerLength"
      next-icon="mdi-menu-right"
      prev-icon="mdi-menu-left"
      :page="nowPage"
      :total-visible="5"
      class="mt-3"
      @input="changePager"
    ></v-pagination>
  </div>
</template>
<script>
import posts from '~/src/posts.json'
export default {
  data () {
    return {
      displayPosts: [],
      pagerLength: 0,
      nowPage: 0
    }
  },
  created(){
    this.displayPosts = posts.index.slice(0, 10)
    this.pagerLength = (posts.index.length % 10 == 0 )? (posts.index.length) / 10 : (Math.floor((posts.index.length) / 10 + 1))
    this.nowPage = 1
  },
  methods:{
    changePager(){
      this.displayPosts.splice(0)
      const target = (this.nowPage-1)*10
      console.log(posts.index.slice(target, target+10))
      posts.index.slice(target, target+10).map((post, idx) =>{
        this.displayPosts.splice(idx, 1, post)
      })
      
    }
  }
}
</script>
<style lang="scss">
.overflow-triple-reader{
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}
.hover-gray{
  background-color: #fafafa;
  &:hover{
    background-color: rgba(0, 0, 0, 0.1)
  }
}
</style>