<template>
  <div id="app" class="container">
    <div class="page-header">
      <h1>Vuejs Firebase Application</h1>
    </div>

    <div class="panel panel-default">
      <div class="panel-heading">
        <h3>Add Book</h3>
      </div>
      <div class="panel-body">
        <form class="form-inline" id="form" v-on:submit.prevent="addBook">
          <div class="form-group">
            <label for="bookTitle">Title:</label>
            <input type="text" id="bookTitle" class="form-control" v-model="newBook.title">
          </div>
          <div class="form-group">
            <label for="bookAuthor">Author:</label>
            <input type="text" id="bookAuthor" class="form-control" v-model="newBook.author">
          </div>
          <div class="form-group">
            <label for="bookUrl">URL:</label>
            <input type="text" id="bookUrl" class="form-control" v-model="newBook.url">
          </div>
          <input type="submit" class="btn btn-primary" value="Add Book">
        </form>
      </div>
    </div>

    <div class="panel panel-default">
      <div class="panel-heading">
        <h3>Books List</h3>
      </div>
      <div class="panel-body">
        <table class="table table-stripe">
          <thead>
            <tr>
              <th>Title</th>
              <th>Author</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="book in books">
              <td><a v-bind:href="book.url">{{book.title}}</a></td>
              <td>{{book.author}}</td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>
</template>

<script>
  import Firebase from 'firebase'

  let config = {
    apiKey: 'AIzaSyBIjfO-0CUe6s5xJTeiAwQ27JbGxv6eaSg',
    authDomain: 'vuejs-a913f.firebaseapp.com',
    databaseURL: 'https://vuejs-a913f.firebaseio.com',
    projectId: 'vuejs-a913f',
    storageBucket: 'vuejs-a913f.appspot.com',
    messagingSenderId: '147251775436'
  }

  let app = Firebase.initializeApp(config)
  let db = app.database()

  let bookRef = db.ref('books')

  export default {
    name: 'app',
    firebase: {
      books: bookRef
    },
    data () {
      return {
        newBook: {
          title: '',
          author: '',
          url: ''
        }
      }
    },
    methods: {
      addBook: function () {
        bookRef.push(this.newBook)
        this.newBook.title = ''
        this.newBook.author = ''
        this.newBook.url = ''
      }
    }
  }
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
