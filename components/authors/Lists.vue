<template>
  <section class="text-gray-600 body-font">
    <div class="container px-5 pt-24 mx-auto">
      <div v-if="sectionTitle" class="flex flex-wrap w-full mb-20">
        <div class="lg:w-1/2 w-full mb-6 lg:mb-0">
          <h1 class="sm:text-3xl text-2xl font-medium title-font mb-2 text-gray-900">{{sectionTitle}}</h1>
          <div class="h-1 w-20 bg-indigo-500 rounded"></div>
        </div>
      </div>
      <div class="flex flex-wrap sm:-m-4 -mx-4 -mb-10 -mt-4 md:space-y-0 space-y-6">
        <div v-for="author in authors" :key="author.id" class="p-4 md:w-1/3 flex flex-col text-center items-center">
          <div class="w-20 h-20 inline-flex items-center justify-center rounded-full bg-indigo-100 text-indigo-500 mb-5 flex-shrink-0">
          <svg fill="none" stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" class="w-10 h-10" viewBox="0 0 24 24">
            <path d="M20 21v-2a4 4 0 00-4-4H8a4 4 0 00-4 4v2"></path>
            <circle cx="12" cy="7" r="4"></circle>
          </svg>
          </div>
          <div class="flex-grow">
            <NuxtLink :to="`/authors/${author.id}`" class="text-gray-900 text-lg title-font font-medium">
              {{author.name}}
            </NuxtLink>
            <h3 class="tracking-widest title-font font-medium text-gray-500">{{author.email}}</h3>
            <h3 class="tracking-widest title-font font-medium text-gray-500 my-2">Total posts: {{author.meta.posts_count}}</h3>
            <p class="leading-relaxed text-base">Blue bottle crucifix vinyl post-ironic four dollar toast vegan taxidermy. Gastropub indxgo juice poutine, ramps microdosing banh mi pug VHS try-hard.</p>
            <a class="mt-3 text-indigo-500 inline-flex items-center">Read More
              <svg fill="none" stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" class="w-4 h-4 ml-2" viewBox="0 0 24 24">
                <path d="M5 12h14M12 5l7 7-7 7"></path>
              </svg>
            </a>
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

      authors: {
        type: [Array],
        default: () => []
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
