<template>
<div>
  <div v-if="$fetchState.pending" class="mt-64 text-xl font-medium text-center">
    <p>Loading...</p>
  </div>
  <div v-else-if="$fetchState.error" class="mt-64 text-xl font-medium text-center text-red-700">
    <p>An error occurred :(</p>
  </div>
  <PostsLists v-else :posts="posts"/>
</div>

</template>

<script>
export default {

  data: () => ({
    posts: []
  }),

  async fetch() {
    this.posts = await this.$axios.$get('blog/posts')
  },
}
</script>
