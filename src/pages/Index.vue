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
          <p>{{ post.node.timeToRead }} min read</p>
          <p>{{ post.node.excerpt }}</p>
        </div>
        <Pagination
          v-if="$page.posts.pageInfo.totalPages > 1"
          :current-page="$page.posts.pageInfo.currentPage"
          :total-pages="$page.posts.pageInfo.totalPages" />
      </div>
    </main>
  </Layout>
</template>

<page-query>
query Posts ($page: Int) {
  posts: allPost (sortBy: "date", order: DESC, perPage: 1, page: $page) @paginate {
    totalCount
    pageInfo {
      totalPages
      currentPage
    }
    edges {
      node {
        title
        date
        timeToRead
        excerpt
        path
      }
    }
  }
}
</page-query>

<script>
import Pagination from '@/components/PaginationPosts'

export default {
  name: 'Landing',
  components: {
    Pagination
  },
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
