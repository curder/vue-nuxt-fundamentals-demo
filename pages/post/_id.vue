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
          <NuxtLink class="text-blue-500 hover:text-blue-700 hover:underline" :to="`/post/${relate.id}`">{{ relate.title }}</NuxtLink>
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

      posts: [
        {
          id: 'what-is-nuxt-js',
          title: 'What is Nuxt JS',
          content: 'Build your next Vue.js application with confidence using NuxtJS. An open source framework making web development simple and powerful.',
        },
        {
          id: 'what-is-vue-js',
          title: 'What is Vue JS',
          content: 'The Progressive JavaScript Framework',
        },
        {
          id: 'what-is-typescript',
          title: 'What is TypeScript',
          content: 'TypeScript extends JavaScript by adding types. <br /> By understanding JavaScript, TypeScript saves you time catching errors and providing fixes before you run code. <br />Any browser, any OS, anywhere JavaScript runs. Entirely Open Source.',
        },
      ],
    };
  },

  mounted() {
    this.post = this.posts.find((item) => item.id === this.id);

    this.related = this.posts.filter((item) => item.id !== this.id);
  },
}
</script>
