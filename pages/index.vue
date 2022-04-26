<template>
  <div class="w-full">
    <div class="flex justify-center pt-20">
      <img
        class="w-1/2 flex"
        src="https://149355165.v2.pressablecdn.com/wp-content/uploads/2014/09/numbers.jpg "
      />
    </div>
    <div
      class="
        -mt-24
        -mb-28
        pl-10
        h-60
        text-5xl text-gray-100
        underline
        font-bold
      "
    >
      The happy numbers blog
    </div>
    <div
      class="
        -mt-40
        -mb-5
        pl-10
        h-28
        text-3xl text-gray-300
      "
    >
    A blog about numbers made by a happy guy! 
    </div>
    <div class="mx-10">
      <div
        class="w-full rounded text-3xl text-gray-100 font-semibold p-5"
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
    </div>
    <div class="mx-10 my-40">
      <div
        class="w-full rounded text-3xl text-gray-100 font-semibold p-5"
        style="background-color: rgb(88, 71, 71); height: 400px"
      >
        Personal favorites:
        <div class="flex flex-wrap justify-start h-80 w-full">
          <div
            @click="goToArticle(article.id)"
            class="w-1/6 m-4 cursor-pointer"
            v-for="article in favoriteArticles"
            :key="article.id"
          >
            <BlogListItem :item="article" class="h-full"></BlogListItem>
          </div>
        </div>
      </div>
    </div>
    <div class="mx-10 my-40">
      <div
        class="w-full rounded text-3xl text-gray-100 font-semibold p-5"
        style="background-color: rgb(88, 71, 71); height: 400px"
      >
        Want more? Click here for a full list of blogs:
        <div class="h-3/4 w-64">
          <nuxt-link to="archives">
            <img
              nuxt
              src="https://upload.wikimedia.org/wikipedia/commons/thumb/c/c8/38254-new_folder-3.svg/1200px-38254-new_folder-3.svg.png"
              class="h-full m-5"
            />
          </nuxt-link>
        </div>
      </div>
    </div>


    <div class="h-1"></div>
  </div>
</template>

<script>
export default {
  name: "IndexPage",
  async asyncData({ $content }) {
    let latestArticles = await $content("articles")
      .without(["body"])
      .sortBy("id", "desc")
      .limit(5)
      .fetch();
    let favoriteArticles = await $content("articles")
      .without(["body"])
      .sortBy("rating", "desc")
      .limit(5)
      .fetch();
    let test = await $content("test-blog").fetch();
    return {
      test,
      latestArticles,
      favoriteArticles,
    };
  },
  methods: {
    goToArticle(id) {
      this.$router.push("/blog-details/" + id);
    }
  },
};
</script>

