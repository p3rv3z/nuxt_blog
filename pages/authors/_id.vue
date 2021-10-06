<template>
  <div>
    <AuthorsSingle :author="author" />
    <PostsLists :posts="author.posts" :section-title="`Author Posts (${author.meta.posts_count})`" />
  </div>
</template>

<script>
  export default {
    async asyncData({$axios, params, redirect}) {
    try {
      const author = await $axios.$get(`blog/authors/${params.id}`)
      return { author }
    } catch (error) {
      redirect('/error')
    }
  },
  }
</script>

<style lang="scss" scoped>

</style>
