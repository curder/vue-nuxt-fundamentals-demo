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
        <li v-for="relate in related" :key="relate.id">
          <NuxtLink :to="{name: 'posts-id', params: {id: relate.id}}"
                    class="text-blue-500 hover:text-blue-700 hover:underline">{{ relate.title }}</NuxtLink>
        </li>
      </ul>
    </aside>
  </div>
</template>
<script>
export default {
  data() {
    return {
      id: this.$route.params.id,

      post: {},
      related: [],

      posts: [],
    };
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

  mounted() {
    this.post = this.$store.state.posts.all.find((item) => item.id === this.id);

    this.related = this.$store.state.posts.all.filter((item) => item.id !== this.id);
  },
}
</script>
