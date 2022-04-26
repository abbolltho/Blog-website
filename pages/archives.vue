<template>
  <div class="pt-40"> 
    <h1 class="text-gray-100 text-5xl mx-auto w-min -mb-3">ARCHIVES</h1>
    <div class="mx-10 p-5 flex flex-row flex-wrap" style="background-color: rgb(88, 71, 71);">
      <div @click="goToArticle(article.id)" class="w-80 m-4 cursor-pointer" v-for="article in articles" :key="article.id">
        <BlogListItem :item="article" class="h-full"></BlogListItem>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  async asyncData({$content}) {
    let articles = await $content('articles').without(['body']).sortBy("id", "desc").fetch()
    return {
      articles
    }
  },
  methods: {
    goToArticle(id) {
      this.$router.push('/blog-details/'+id)
    }
  }
}
</script>