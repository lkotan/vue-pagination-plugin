<template>
  <div id="app">
    <Pagination
      :totalPage="3"
      :perPage="4"
      :initialPage="currentPage"
      @changePage="changePage"
      pills
      size="sm"
    />
  </div>
</template>

<script>
import Pagination from "@/components/Pagination";
export default {
  name: "App",
  components: {
    Pagination,
  },
  data() {
    return {
      currentPage: 1,
    };
  },
  methods: {
    changePage(page) {
      this.currentPage = page;
    },
  },
};
</script>

<style></style>
