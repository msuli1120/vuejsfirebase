<template>
  <div id="app">

  </div>
</template>

<script>
  import Hello from './components/Hello'
  import Firebase from 'firebase'

  let config = {
    apiKey: 'AIzaSyBIjfO-0CUe6s5xJTeiAwQ27JbGxv6eaSg',
    authDomain: 'vuejs-a913f.firebaseapp.com',
    databaseURL: 'https://vuejs-a913f.firebaseio.com',
    projectId: 'vuejs-a913f',
    storageBucket: 'vuejs-a913f.appspot.com',
    messagingSenderId: '147251775436',
  }

  let app = Firebase.initializeApp(config)
  let db = app.database()

  let bookRef = db.ref('books')

  export default {
    name: 'app',
    firebase: {
     books: bookRef
    }
  }
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
