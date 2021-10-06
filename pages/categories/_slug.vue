<template>
  <div>
    <PostsLists :posts="category.posts" :section-title="`${category.name} (${category.meta.posts_count})`" />
  </div>
</template>

<script>
  export default {
    async asyncData({$axios, params, redirect}) {
      try {
        const category = await $axios.$get(`blog/categories/${params.slug}`)
        return { category }
      } catch (error) {
        redirect('/error')
      }
    },
  }
</script>

<style lang="scss" scoped>

</style>
