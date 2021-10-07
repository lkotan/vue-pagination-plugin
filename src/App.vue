<template>
  <div id="app">
    <header>
      <button @click="pills = !pills">Toggle Pills</button>
      <input type="text" v-model="size" />
    </header>
    <section class="cards">
      <h3 v-for="(item, index) in paginateData" :key="index">
        {{ item.name }}
      </h3>
    </section>
    <Pagination
      :totalPage="totalPage"
      :perPage="perPage"
      :initialPage="currentPage"
      @changePage="changePage"
      :pills="pills"
      :size="size"
      :pageRange="pageRange"
      :breakText="breakText"
      :marginPages="marginPages"
    >
    </Pagination>
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
      perPage: 3,
      totalPage: 0,
      pills: false,
      size: "md",
      pageRange: 3,
      marginPages: 2,
      breakText: "...",
      data: [
        {
          name: "Bret",
          email: "bret@gmail.com",
          phone: "1580 1308926",
          department: "Software",
        },
        {
          name: "Antonette",
          email: "antonette@gmail.com",
          phone: "1580 1308926",
          department: "Customer Service",
        },
        {
          name: "Bret",
          email: "bret@gmail.com",
          phone: "1580 1308926",
          department: "Software",
        },
        {
          name: "Antonette",
          email: "antonette@gmail.com",
          phone: "1580 1308926",
          department: "Customer Service",
        },
        {
          name: "Bret",
          email: "bret@gmail.com",
          phone: "1580 1308926",
          department: "Software",
        },
        {
          name: "Antonette",
          email: "antonette@gmail.com",
          phone: "1580 1308926",
          department: "Customer Service",
        },
        {
          name: "Bret",
          email: "bret@gmail.com",
          phone: "1580 1308926",
          department: "Software",
        },
        {
          name: "Antonette",
          email: "antonette@gmail.com",
          phone: "1580 1308926",
          department: "Customer Service",
        },
        {
          name: "Samantha",
          email: "samantha@gmail.com",
          phone: "1580 1308926",
          department: "Software",
        },
        {
          name: "Karianne",
          email: "karianne@gmail.com",
          phone: "1580 1308926",
          department: "Customer Service",
        },
        {
          name: "Kamren",
          email: "kamren@gmail.com",
          phone: "1580 1308926",
          department: "Human Resources",
        },
        {
          name: "Dennis",
          email: "dennis@gmail.com",
          phone: "1580 1308926",
          department: "Human Resources",
        },
        {
          name: "Kurtis",
          email: "kurtis@gmail.com",
          phone: "1580 1308926",
          department: "Human Resources",
        },
        {
          name: "Nicholas",
          email: "nicholas@gmail.com",
          phone: "1580 1308926",
          department: "Human Resources",
        },
        {
          name: "Glenna",
          email: "glenna@gmail.com",
          phone: "1580 1308926",
          department: "Software",
        },
        {
          name: "Clementina",
          email: "clementina@gmail.com",
          phone: "1580 1308926",
          department: "Customer Service",
        },
        {
          name: "Brad",
          email: "brad@gmail.com",
          phone: "1580 1308926",
          department: "Software",
        },
        {
          name: "Krasimir",
          email: "krasimir@gmail.com",
          phone: "1580 1308926",
          department: "Human Resources",
        },
        {
          name: "Mark",
          email: "mark@gmail.com",
          phone: "1580 1308926",
          department: "Software",
        },
        {
          name: "Kia",
          email: "kia@gmail.com",
          phone: "1580 1308926",
          department: "Software",
        },
        {
          name: "Josh",
          email: "josh@gmail.com",
          phone: "1580 1308926",
          department: "Customer Service",
        },
        {
          name: "Rasmus",
          email: "rasmus@gmail.com",
          phone: "1580 1308926",
          department: "Human Resources",
        },
        {
          name: "Jim",
          email: "jim@gmail.com",
          phone: "1580 1308926",
          department: "Software",
        },
        {
          name: "George",
          email: "george@gmail.com",
          phone: "1580 1308926",
          department: "Software",
        },
        {
          name: "Ankur",
          email: "ankur@gmail.com",
          phone: "1580 1308926",
          department: "Software",
        },
        {
          name: "Simon",
          email: "simon@gmail.com",
          phone: "1580 1308926",
          department: "Human Resources",
        },
        {
          name: "Evan",
          email: "evan@gmail.com",
          phone: "1580 1308926",
          department: "Customer Service",
        },
        {
          name: "Kass",
          email: "kass@gmail.com",
          phone: "1580 1308926",
          department: "Customer Service",
        },
        {
          name: "George",
          email: "george@gmail.com",
          phone: "1580 1308926",
          department: "Software",
        },
        {
          name: "Michelle",
          email: "michelle@gmail.com",
          phone: "1580 1308926",
          department: "Software",
        },
      ],
    };
  },
  created() {
    this.totalPage = Math.ceil(this.data.length / this.perPage);
  },
  computed: {
    paginateData() {
      return this.data.slice(
        this.perPage * this.currentPage - this.perPage,
        this.perPage * this.currentPage
      );
    },
  },
  methods: {
    changePage(page) {
      this.currentPage = page;
    },
  },
};
</script>

<style>
body {
  background: #e7e7e7;
}
#app {
  margin-top: 50px;
  display: flex;
  flex-direction: column;
  align-items: center;
}
button {
  outline: none;
  cursor: pointer;
  padding: 6px 8px;
  border: 1px solid #40ae7d;
  background: white;
  color: #40ae7d;
}
header {
  display: flex;
  flex-direction: column;
  margin-bottom: 20px;
}
header button {
  margin-bottom: 8px;
  border-radius: 10px;
  font-weight: 600;
  border: 1px solid #e1e1e1;
}
.cards {
  padding: 10px 50px;
  margin-bottom: 10px;
  border-radius: 4px;
  color: white;
  background: #40ae7d;
}
.cards h3 {
  margin: 8px;
}
</style>
