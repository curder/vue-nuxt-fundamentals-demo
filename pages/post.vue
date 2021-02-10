<template>
  <div class="container">
    <article>
      <h1 class="title">What is Nuxt.js?</h1>
      <p>Build your next Vue.js application with confidence using NuxtJS. An open source framework making web development simple and powerful.</p>
    </article>
  </div>
</template>

<script>
export default {
}
</script>

<style>
.container {
  @apply mx-auto flex justify-center items-center leading-normal;
}

.title {
  @apply font-bold text-3xl text-yellow-600;
}

article * {
  @apply mb-4;
}
</style>
