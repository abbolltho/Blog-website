<template>
  <div class="mx-10 pt-28">
    <div class="flex justify-center ">
        <h1 class="text-5xl mb-8 underline text-gray-100">{{ article.title }}</h1>
    </div>
    
    <div class="flex justify-center">
        <p class="text-2xl mb-8 text-gray-200">{{ article.description }}</p>
    </div>
    
    <div class="rounded p-3 mb-40" style="background-color: rgb(88, 71, 71); height: 600px">
      <div class="rounded p-3 h-full w-max mx-auto" style="background-color: rgb(81, 58, 58)">
        <img class="max-h-full" :src="article.image" />
      </div>
    </div>

    <div class="rounded p-3 pb-10 mb-40" style="background-color: rgb(88, 71, 71)">
      <nuxt-content :document="article" class="text-lg text-gray-300"></nuxt-content>
    </div>

    <div class="h-1"></div>

  </div>
</template>
<script>
export default {
  async asyncData({ $content}) {
    let article = await $content("about-me").fetch();
    return {
      article,
    };
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