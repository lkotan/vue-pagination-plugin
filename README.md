# pagination

# Properties


| Property    | Type    | Default | Required | Description                                    |
|-------------|---------|---------|----------|------------------------------------------------|
| totalPage   | Number  |         | True     | Total number of rows in the dataset            |
| perPage     | Number  |         | True     | Number of rows per page                        |
| initialPage | Number  |         | True     | Number of rows initial page                    |
| pills       | Boolean | False   | False    | Applies pill styling to the pagination buttons |
| size        | String  | md      | False    | Size of the rendered buttons                   |

# Vue

```bash
data() {
    return {
            currentPage: 1,
            perPage: 4,
            totalPage: 0,
            pills: false,
            size: "md",
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
      :pills="pills"
      :size="size"
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
