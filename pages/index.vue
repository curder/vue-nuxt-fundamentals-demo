<template>
  <div class="container">
    <div class="space-y-8">
      <Logo/>
      <h1 class="title">
        Nuxt Fundamentals
      </h1>
      <div class="links space-x-6">
        <NuxtLink v-for="post in posts" :key="post.id"
                  :to="{name: 'posts-id', params: {id: post.id}}"
                  v-text="post.title"
                  class="button--green text-blue-600 hover:text-blue-700">
        </NuxtLink>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
        posts: [],
    };
  },

  head() {
      return {
        title: 'Home Page - Nuxt Fundamentals',
      }
  },

  created() {
    this.posts = this.$store.state.posts.all;
  }
}
</script>
<style>
/* Sample `apply` at-rules with Tailwind CSS
.container {
@apply min-h-screen flex justify-center items-center text-center mx-auto;
}
*/
.container {
  @apply flex mx-auto min-h-screen justify-center items-center text-center;
}

.title {
  font-family: 'Quicksand',
  'Source Sans Pro',
  -apple-system,
  BlinkMacSystemFont,
  'Segoe UI',
  Roboto,
  'Helvetica Neue',
  Arial,
  sans-serif;
  @apply block font-light;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  @apply font-light;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
