<template>
<!-- v-theme vrednost sa duplim i jednotrukim navodnicima -->
  <div v-theme:column="'narrow'" id="show-blogs">
      <h1  class="blogs-title">Show blogs</h1>
       <input type="text" placeholder="search" v-model="search">
       <!-- div bez search filtera: -->
      <!-- <div v-for="blog in blogs" :key="blog" class="single-blog">
          <h2 v-rainbow>{{ blog.title | to-uppercase }}</h2>
          <article class="blog-body">{{ blog.body | snippet }}</article>
      </div> -->

      <div v-for="blog in filteredBlogs" :key="blog" class="single-blog">
          <h2 v-rainbow>{{ blog.title | to-uppercase }}</h2>
          <article class="blog-body">{{ blog.body | snippet }}</article>
      </div>
  </div>
</template>

<script>

export default {
    
  data () {
    return {
      blogs: [],
      search: ''
    }
  },
  methods: {
      
  },
  created() {
      this.$http.get('https://jsonplaceholder.typicode.com/posts').then(function(data) {
          this.blogs = data.body.slice(0,10);
      });
  },
  computed: {
      filteredBlogs: function() {
          return this.blogs.filter((blog) => {
              return blog.title.match(this.search);
          });
      }
  }
}
</script>

<style>
  #show-blogs *{
    box-sizing: border-box;
}
#show-blogs {
    margin: 20px auto;
    /* max-width: 500px; */
}
label{
    display: block;
    margin: 20px 0 10px;
}
input[type="text"], textarea{
    display: block;
    width: 100%;
    padding: 8px;
}
#preview{
    padding: 10px 20px;
    border: 1px dotted #ccc;
    margin: 30px 0;
}
h3{
    margin-top: 10px;
}
#checkboxes input {
    display: inline-block;
    margin-right: 10px;
}
#checkboxes label {
    display: inline-block;
}
.blogs-title {
    text-align: center;
    color: white;
    background: olivedrab;
    padding: 5px;
    text-transform: uppercase;
    border-radius: 5px;
}
.blog-body {
    background: rgb(50, 50, 50);
    color: white;
    padding: 9px;
    border-radius: 5px;
}
</style>