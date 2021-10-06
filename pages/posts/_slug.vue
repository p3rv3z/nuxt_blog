<template>
  <div>
    <PostsSingle :post="post" />
  </div>
</template>

<script>
  export default {
    async asyncData({$axios, params, redirect}) {
    try {
      const post = await $axios.$get(`blog/posts/${params.slug}`)
      return { post }
    } catch (error) {
      redirect('/error')
    }
  },
  }
</script>

<style lang="scss" scoped>

</style>
