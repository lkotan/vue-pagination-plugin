<template>
  <div class="pagination">
    <div v-for="page in totalPage" :key="page" :class="[pills ? 'pills' : '']">
      <button
        class="prev"
        :style="buttonSize"
        v-if="page == 1"
        :disabled="currentPage == page ? true : false"
        @click="currentPage--, $emit('changePage', currentPage)"
      >
        Prev
      </button>
      <button
        :style="buttonSize"
        :class="[initialPage == page ? 'active' : '']"
        @click="(currentPage = page), $emit('changePage', currentPage)"
      >
        {{ page }}
      </button>
      <button
        class="next"
        :style="buttonSize"
        v-if="page == totalPage"
        :disabled="currentPage == totalPage ? true : false"
        @click="currentPage++, $emit('changePage', currentPage)"
      >
        Next
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: "Pagination",
  props: {
    totalPage: {
      type: Number,
      required: true,
    },
    perPage: { type: Number, required: true },
    initialPage: { type: Number, required: true },
    pills: {
      type: Boolean,
      default: false,
    },
    size: {
      type: String,
      default: "md",
    },
  },
  data() {
    return {
      currentPage: this.initialPage,
    };
  },
  computed: {
    buttonSize() {
      let buttonStyle = "";
      switch (this.size) {
        case "sm":
          buttonStyle = { fontSize: "12px" };
          break;
        case "md":
          buttonStyle = { fontSize: "16px" };
          break;
        case "lg":
          buttonStyle = { fontSize: "20px" };
          break;
        default:
          buttonStyle = { fontSize: "16px" };
          break;
      }
      return buttonStyle;
    },
  },
};
</script>

<style scoped>
.pagination {
  display: flex;
}
.pills button {
  border-radius: 50%;
  margin-left: 4px;
}
.pills .next,
.pills .prev {
  border-radius: 6px;
}
.active {
  color: white;
  background: #40ae7d;
}
</style>
