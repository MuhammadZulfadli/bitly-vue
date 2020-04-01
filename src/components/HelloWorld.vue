<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <div class="container">
    <h1 class="text-center">URL Shortener</h1>
    <form action="/shortUrls" method="POST">
      <div class="form-group">
        <label for="exampleInputEmail1">Your URL</label>
        <input required placeholder="URL" type="url" name ="fullUrl" class="form-control" id="fullUrl" aria-describedby="urlHelp">
        <small id="emailHelp" class="form-text text-muted">URL</small>
      </div>
      <button type="submit" class="btn btn-primary">Submit</button>
    </form>
    <br>

      <table class="table table-hover">
        <thead>
          <tr>
            <th>Full URL</th>
            <th>Short URL</th>
            <th>Clicks</th>
          </tr>
        </thead>
          
      </table>
    </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'HelloWorld',
  data() {
    return {

    shortUrls: [],
  }
},

async mounted(){
    this.load()
  },

  method:{
    async load() {
      const response  = await axios.post('http://localhost:3000/')
      response.data = response.shortUrls
    }
  }
    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
