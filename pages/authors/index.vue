<template>
<div>
  <div v-if="$fetchState.pending" class="mt-64 text-xl font-medium text-center">
    <p>Loading...</p>
  </div>
  <div v-else-if="$fetchState.error" class="mt-64 text-xl font-medium text-center text-red-700">
    <p>An error occurred :(</p>
  </div>
  <AuthorsLists v-else :authors="authors"/>
</div>

</template>

<script>
export default {

  data: () => ({
    authors: []
  }),

  async fetch() {
    this.authors = await this.$axios.$get('blog/authors')
  },
}
</script>
