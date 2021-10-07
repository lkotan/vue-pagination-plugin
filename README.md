# pagination

Demo [Pagination-Plugin](https://vue-pagination-plugin.vercel.app/)
# Properties


| Property    | Type    | Default | Required | Description                                    |
|-------------|---------|---------|----------|------------------------------------------------|
| totalPage   | Number  |         | True     | Total number of rows in the dataset            |
| perPage     | Number  |         | True     | Number of rows per page                        |
| initialPage | Number  |         | True     | Number of rows initial page                    |
| pills       | Boolean | False   | False    | Applies pill styling to the pagination buttons |
| size        | String  | md      | False    | Size of the rendered buttons                   |
| pageRange   | Number  | 3       | False    | Range of pages which displayed                 |
| breakText   | String  | ...     | False    | Text for the break view indicator              |
| marginPage  | Number  | 2       | False    | The number of displayed pages for margins      |

# Vue

```bash
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
        };
},
methods: {
    changePage(page) {
        this.currentPage = page;
    }
}
```
# Props
```bash
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
    />
```
# Emit

```bash
<Pagination @changePage="changePage"/>
```


## Project setup

```
npm install
```

### Compiles and hot-reloads for development

```
npm run serve
```

### Compiles and minifies for production

```
npm run build
```

### Lints and fixes files

```
npm run lint
```

### Customize configuration

See [Configuration Reference](https://cli.vuejs.org/config/).
