<template>
  <section class="text-gray-600 body-font">
    <div class="container px-5 pt-24 mx-auto">
      <div v-if="sectionTitle" class="flex flex-wrap w-full mb-20">
        <div class="lg:w-1/2 w-full mb-6 lg:mb-0">
          <h1 class="sm:text-3xl text-2xl font-medium title-font mb-2 text-gray-900">{{sectionTitle}}</h1>
          <div class="h-1 w-20 bg-indigo-500 rounded">
          </div>
        </div>
      </div>
      <div class="flex flex-wrap -m-4">
        <div v-for="post in posts" :key="post.id" class="p-4 md:w-1/3">
          <div class="h-full border-2 border-gray-200 border-opacity-60 rounded-lg overflow-hidden">
            <img class="lg:h-48 md:h-36 w-full object-cover object-center" src="https://dummyimage.com/720x400" alt="blog">
            <div class="p-6">
              <div v-if="hasCategory(post)" class="my-2">
                <NuxtLink v-for="category in post.categories" :key="category.id" :to="`/categories/${category.slug}`" class="inline-flex items-center justify-center px-2 py-1 last:mr-0 mr-2 text-xs font-bold leading-none text-indigo-700 bg-indigo-200 rounded">
                  {{category.name}}
                </NuxtLink>
              </div>
              <NuxtLink :to="`/posts/${post.slug}`" class="title-font text-lg font-medium text-gray-900 mb-3">{{post.title}}</NuxtLink>
              <div class="flex mt-1 mb-4">
                <span class="title-font font-medium text-gray-500">By &nbsp;</span>
                <NuxtLink v-if="post.author" :to="`/authors/${post.author.id}`" class="title-font font-medium text-indigo-700">{{post.author.name}} </NuxtLink>
                <span class="title-font font-medium text-gray-500 block">&nbsp; On {{post.created_at}}</span>
              </div>
              <p class="leading-relaxed mb-3">{{post.body}}</p>
              <div class="flex items-center flex-wrap ">
                <a class="text-indigo-500 inline-flex items-center md:mb-2 lg:mb-0">Read More
                  <svg class="w-4 h-4 ml-2" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2" fill="none" stroke-linecap="round" stroke-linejoin="round">
                    <path d="M5 12h14"></path>
                    <path d="M12 5l7 7-7 7"></path>
                  </svg>
                </a>
                <span class="text-gray-400 mr-3 inline-flex items-center lg:ml-auto md:ml-0 ml-auto leading-none text-sm pr-3 py-1 border-r-2 border-gray-200">
                  <svg class="w-4 h-4 mr-1" stroke="currentColor" stroke-width="2" fill="none" stroke-linecap="round" stroke-linejoin="round" viewBox="0 0 24 24">
                    <path d="M1 12s4-8 11-8 11 8 11 8-4 8-11 8-11-8-11-8z"></path>
                    <circle cx="12" cy="12" r="3"></circle>
                  </svg>1.2K
                </span>
                <span class="text-gray-400 inline-flex items-center leading-none text-sm">
                  <svg class="w-4 h-4 mr-1" stroke="currentColor" stroke-width="2" fill="none" stroke-linecap="round" stroke-linejoin="round" viewBox="0 0 24 24">
                    <path d="M21 11.5a8.38 8.38 0 01-.9 3.8 8.5 8.5 0 01-7.6 4.7 8.38 8.38 0 01-3.8-.9L3 21l1.9-5.7a8.38 8.38 0 01-.9-3.8 8.5 8.5 0 014.7-7.6 8.38 8.38 0 013.8-.9h.5a8.48 8.48 0 018 8v.5z"></path>
                  </svg>6
                </span>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
  export default {
    props: {
      sectionTitle: {
        type: String,
        default: ''
      },

      posts: {
        type: [Array],
        default: () => []
      },

    },

    methods: {
      hasCategory(post) {
        if (post.categories)
          return post.categories.length > 0
        else
          return 0
      }
    },
  }
</script>

<style lang="scss" scoped>

</style>
