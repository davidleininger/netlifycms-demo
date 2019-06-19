<template>
  <div class="flex">
    <g-link :to="previousPage" v-if="showPreviousPage">&larr; Prev</g-link>
    <div class="text-base">Page {{ currentPage }} of {{ totalPages }}</div>
    <g-link :to="nextPage" v-if="showNextPage">Next &rarr;</g-link>
  </div>
</template>

<script>
export default {
  props: ['base', 'totalPages', 'currentPage'],
  computed: {
    showPreviousPage() {
      return this.currentPage !== 1
    },
    previousPage() {
      return [0, 1].includes(this.currentPage - 1)
        ? `/`
        : `${this.basePath}/${this.currentPage - 1}`;
    },
    showNextPage() {
      return this.currentPage !== this.totalPages
    },
    nextPage(currentPage, totalPages) {
      return this.totalPages > this.currentPage
        ? `${this.basePath}/${this.currentPage + 1}`
        : `${this.basePath}/${this.currentPage}`;
    },
    basePath() {
      return this.base === undefined ? `` : `${this.base}`
    }
  }
}
</script>
