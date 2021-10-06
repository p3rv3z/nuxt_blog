<template>
	<section class="text-gray-600 body-font">
    <div class="container mx-auto flex px-5 pt-24 items-center justify-center flex-col">
      <img class="lg:w-2/6 md:w-3/6 w-5/6 mb-10 object-cover object-center rounded" alt="hero" src="https://dummyimage.com/720x600">
      <div class="lg:w-2/3 w-full">
        <div v-if="hasCategory(post)" class="flex items-center mb-4">
            <span class="mr-2 font-bold leading-none text-gray-500">Categories: </span>
            <span v-for="category in post.categories" :key="category.id" class="inline-flex items-center justify-center px-2 py-1 last:mr-0 mr-2 text-xs font-bold leading-none text-indigo-700 bg-indigo-200 rounded">
              {{category.name}}
            </span>
        </div>

        <h1 class="title-font sm:text-4xl text-3xl mb-4 font-medium text-gray-900">{{post.title}}</h1>
        <div class="flex mb-4">
          <span class="title-font font-medium text-gray-500">By &nbsp;</span>
          <NuxtLink v-if="post.author" :to="`/authors/${post.author.id}`" class="title-font font-medium text-indigo-700">{{post.author.name}} </NuxtLink>
          <span class="title-font font-medium text-gray-500 block">&nbsp; On {{post.created_at}}</span>
        </div>

        <p class="mb-8 leading-relaxed">{{post.body}}</p>
      </div>
    </div>
  </section>
</template>

<script>
  export default {
    props: {
      post: {
        type: Object,
        default: () => {}
      },
    },

    methods: {
      hasCategory(post) {
        return post.categories.length > 0
      }
    },
  }
</script>

<style lang="scss" scoped>

</style>
