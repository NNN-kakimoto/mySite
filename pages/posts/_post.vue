<template>
  <div>
    <div class="py-10 px-5" v-html="post"></div>
  </div>
</template>

<script>
import posts from '~/src/posts.json'
  export default {  
    computed: {
      post() {
        if (false == posts.paths.includes(this.$route.params.post)){
          this.$nuxt.error({
            statusCode: 404,
            message: '404 Not Found'
          })
          return null
        }
        
        const post = Object.assign({}, require(`~/src/posts/${this.$route.params.post}.md`));
        console.log(post)
        return post.default
      }
    },
    // validate({ params }) {
    //   return sourceFileArray.includes(`content/posts/${params.date}-${params.slug}.md`);
    // },
    // asyncData({ params }) {
    //   return Object.assign({}, require(`~/src/posts/${params.post}.md`), { params });
    // },
    created(){
      console.log(this.$route.params.post)
    }
  }
</script>
<style lang="scss">
</style>