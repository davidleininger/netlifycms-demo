<template>
  <Layout>
    <main>
      <g-image alt="Example image" src="~/favicon.png" width="135" />

      <h1>Hello, world!</h1>

      <p>
        Lorem ipsum dolor sit amet, consectetur adipisicing elit. Pariatur excepturi labore tempore expedita, et iste tenetur suscipit explicabo! Dolores, aperiam non officia eos quod asperiores
      </p>

      <div class="feed">
        <div v-for="post in $page.posts.edges" :key="post.path">
          <g-link :to="post.node.path"><h3>{{ post.node.title }}</h3></g-link>
          <p>{{ post.node.excerpt }}</p>
        </div>
      </div>
    </main>
  </Layout>
</template>

<page-query>
query Posts ($page: Int) {
  posts: allPost (sortBy: "date", order: DESC, perPage: 3, page: $page) {
    totalCount
    pageInfo {
      totalPages
      currentPage
    }
    edges {
      node {
        title
        date
        excerpt
        path
      }
    }
  }
}
</page-query>

<script>
export default {
  metaInfo: {
    title: 'Netlify CMS Starter'
  }
}
</script>

<style>
.home-links a {
  margin-right: 1rem;
}
</style>
