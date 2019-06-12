<template>
  <Layout>
    <h1>{{ $page.post.title }}</h1>
    <p>{{ $page.post.timeToRead }}</p>
    <div class="post" v-html="$page.post.content" />
  </Layout>
</template>

<page-query>
query Post($path: String!) {
  post(path: $path) {
    title
    date (format: "MMMM D, Y")
    timeToRead
    content
  }
}
</page-query>

<script>
export default {
  name: 'Post',
  metaInfo() {
    return {
      title: this.$page.post.title
    }
  }
}
</script>

<style>
.post img{
  height: auto;
  max-width: 100%;
}
</style>
