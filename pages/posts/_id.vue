<template>
  <div class="min-h-screen mx-auto flex justify-center items-center leading-normal">
    <div class="flex flex-col space-y-8">
      <Logo/>
      <article class="text-center">
        <h1 class="mb-4 font-bold text-3xl text-yellow-600">{{ post.title }}</h1>
        <p class="mb-4 max-w-3xl text-gray-700" v-html="post.content"></p>
      </article>
    </div>
    <aside>
      <h2 class="text-2xl text-yellow-600 font-medium">Post you might enjoy</h2>
      <ul>
        <li v-for="post in related_posts" :key="post.id">
          <NuxtLink :to="{name: 'posts-id', params: {id: post.id}}"
                    class="text-blue-500 hover:text-blue-700 hover:underline">{{ post.title }}
          </NuxtLink>
        </li>
      </ul>
    </aside>
  </div>
</template>
<script>
export default {
  async asyncData({app, params}) {
    return {
      post: app.store.state.posts.all.find((item) => item.id === params.id),
      related_posts: app.store.state.posts.all.filter((item) => item.id !== params.id),
    }
  },

  head() {
    return {
      title: `${this.post.title} - Nuxt Fundamentals`,
      meta: [
        {name: "twitter:title", content: this.post.title},
        {name: "twitter:description", content: this.post.content},
      ]
    }
  },
}
</script>
