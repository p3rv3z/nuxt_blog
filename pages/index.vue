<template>
  <div>
    <div v-if="$fetchState.pending" class="mt-64 text-xl font-medium text-center">
      <p>Loading...</p>
    </div>
    <div v-else-if="$fetchState.error" class="mt-64 text-xl font-medium text-center text-red-700">
      <p>An error occurred :(</p>
    </div>
    <div v-else>
      <PostsLists :posts="posts"/>
      <AuthorsLists :authors="authors" section-title="Popular Authors"/>
    </div>
  </div>
</template>

<script>
export default {
  data: () => ({
    posts: [],
    authors: []
  }),

  async fetch() {
    this.posts = await this.$axios.$get('blog/home/posts')
    this.authors = await this.$axios.$get('blog/home/authors')
  },
}
</script>
