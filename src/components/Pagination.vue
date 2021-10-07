<template>
  <div class="pagination">
    <div
      v-for="(page, index) in pages"
      :key="index"
      :class="[pills ? 'pills' : '']"
    >
      <button
        class="prev"
        :class="[currentPage == page.text ? 'disabled' : '']"
        :style="buttonSize"
        v-if="page.text == 1"
        :disabled="currentPage == page.text ? true : false"
        @click="currentPage--, $emit('changePage', currentPage)"
      >
        Prev
      </button>
      <button class="break" v-if="page.breakView">{{ breakText }}</button>
      <button
        v-else
        :style="buttonSize"
        :class="[initialPage == page.text ? 'active' : '']"
        @click="(currentPage = page.text), $emit('changePage', currentPage)"
      >
        {{ page.text }}
      </button>
      <button
        class="next"
        :class="[currentPage == totalPage ? 'disabled' : '']"
        :style="buttonSize"
        v-if="page.text == totalPage"
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
    pageRange: {
      type: Number,
      default: 3,
    },
    breakText: {
      type: String,
      default: "...",
    },
    marginPages: {
      type: Number,
      default: 2,
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
    pages() {
      let items = {};
      if (this.totalPage <= this.pageRange) {
        for (let index = 0; index < this.totalPage; index++) {
          let page = {
            index: index,
            text: index + 1,
          };
          items[index] = page;
        }
      } else {
        const halfPageRange = Math.floor(this.pageRange / 2);

        let pageItem = (index) => {
          let page = {
            index: index,
            text: index + 1,
          };
          items[index] = page;
        };

        for (let i = 0; i < this.marginPages; i++) pageItem(i);

        let breakView = (index) => {
          let breakView = {
            disabled: true,
            breakView: true,
          };
          items[index] = breakView;
        };

        let selectedRangeLow = 0;
        if (this.initialPage - halfPageRange > 0)
          selectedRangeLow = this.initialPage - 1 - halfPageRange;

        let selectedRangeHigh = selectedRangeLow + this.pageRange - 1;
        if (selectedRangeHigh >= this.totalPage) {
          selectedRangeHigh = this.totalPage - 1;
          selectedRangeLow = selectedRangeHigh - this.pageRange + 1;
        }

        for (
          let i = selectedRangeLow;
          i <= selectedRangeHigh && i <= this.totalPage - 1;
          i++
        )
          pageItem(i);

        if (selectedRangeLow > this.marginPages) breakView(selectedRangeLow - 1);
        if (selectedRangeHigh + 1 < this.totalPage - this.marginPages)
          breakView(selectedRangeHigh + 1);

        for (
          let i = this.totalPage - 1;
          i >= this.totalPage - this.marginPages;
          i--
        )
          pageItem(i);
      }
      return items;
    },
  },
};
</script>

<style scoped>
.pagination {
  display: flex;
}

.pagination .break {
  display: flex;
  height: 100%;
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
.disabled {
  cursor: not-allowed;
}
</style>
