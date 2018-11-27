<template>
  <div>
    <ul>
        <li v-for="book in books">
            <router-link :to="'/books/' + book.id">{{ book.title }}</router-link>
        </li>
    </ul>
  </div>
</template>

<script>
    export default {
        created() {
            console.log(`this = ${this.$http}`);
            this.fetchBooks()
        },
        data() {
            return {
                books: []
            }
        },
        methods: {
            fetchBooks() {
                this.$http.get('/api/books')
                .then(res =>  {
                    this.books = res.data
                })
            }
        }
    }
</script>