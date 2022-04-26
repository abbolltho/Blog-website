<template>
  <div class="mx-10 pt-28">
    <div class="flex justify-center ">
        <h1 class="text-5xl mb-8 underline text-gray-100">{{ article.title }}</h1>
    </div>
    
    <div class="flex justify-center">
        <p class="text-2xl mb-8 text-gray-200">{{ article.description }}</p>
    </div>
    
    <div class="rounded p-3 mb-40" style="background-color: rgb(88, 71, 71); height: 600px">
      <div class="rounded p-3 pb-10 h-full w-max mx-auto" style="background-color: rgb(81, 58, 58)">
        <img class="max-h-full" :src="article.image" />
        <p class="mt-1 text-gray-400 text-lg">{{article.imageText}}</p>
      </div>
    </div>

    <div class="rounded p-3 pb-10 mb-40" style="background-color: rgb(88, 71, 71)">
      <nuxt-content :document="article" class="text-lg text-gray-300"></nuxt-content>
    </div>
    

    <div
      class="w-full rounded text-3xl text-gray-100 font-semibold p-5 mb-40"
      style="background-color: rgb(88, 71, 71); height: 400px"
    >
      Latest Articles:

      <div class="flex flex-wrap justify-start h-80 w-full">
        <div
          @click="goToArticle(article.id)"
          class="w-1/6 m-4 cursor-pointer"
          v-for="article in latestArticles"
          :key="article.id"
        >
          <BlogListItem :item="article" class="h-full"></BlogListItem>
        </div>
      </div>
    </div>

    <div class="h-1"></div>

  </div>
</template>
<script>
export default {
  async asyncData({ $content, params }) {
    let article = await $content("articles/article" + params.id).fetch();
    let latestArticles = await $content("articles")
      .without(["body"])
      .sortBy("id", "desc")
      .limit(5)
      .fetch();
    return {
      article,
      latestArticles
    };
  },
  methods: {
    goToArticle(id) {
      this.$router.push("/blog-details/" + id);
    }
  },
};
</script>

<style>
.blogImg{
  padding: 12px;
  margin: 8px;
  background-color: rgb(81, 58, 58);
  border-radius: 4px;
  margin-right: auto;
  margin-left: auto;
}
</style>