<template>
  <div id="add-blog">
      <h2>Add new blog post</h2>
      <form v-if="!submitted">
        <label>Blog title</label>
        <input type="text" v-model.lazy="blog.title" required>
        <label>Blog content</label>
        <textarea v-model.lazy="blog.content"></textarea>
        <div id="checkboxes">
            <label>Users</label>
            <input type="checkbox" value="users" v-model="blog.categories">
            <label>Wizards</label>
            <input type="checkbox" value="wizards" v-model="blog.categories">
            <label>Mirko</label>
            <input type="checkbox" value="mirko" v-model="blog.categories">
            <label>Lood</label>
            <input type="checkbox" value="lood" v-model="blog.categories">
        </div>
        <label>Author :</label>
        <select v-model="blog.author">
            <option v-for="auth in authors" :key="auth">{{ auth }}</option>
        </select>
        <button v-on:click.prevent="post">Add Blog</button>
      </form>
      <div v-if="submitted">
          <h4>Successfully submitted ...</h4>
      </div>
      <div id="preview">
          <h3>Preview blog</h3>
          <p>Blog title : {{ blog.title }}</p>
          <p>Blog content:</p>
          <p>{{ blog.content }}</p>
          {{ boo }}
          <p>Author : {{ blog.author }}</p>
          <ol>
              <li v-for="cat in blog.categories" :key="cat">{{ cat }}</li>
          </ol>
         
      </div>
  </div>
</template>

<script>

export default {
    props: ['boo'],
  data () {
    return {
      blog: {
          title: '',
          content: '',
          categories: [],
          author: ''
      },
      authors: ['miki','viki','ziki'],
      submitted: false
    }
  },
  methods: {
      post: function() {
          this.$http.post('https://jsonplaceholder.typicode.com/posts',{
              title: this.blog.title,
              body: this.blog.content,
              userId: 1
          }).then(function(data){
            //   console.log(data);
            this.submitted = true;
          });
      }
  }
}
</script>

<style>
  #add-blog *{
    box-sizing: border-box;
}
#add-blog{
    margin: 20px auto;
    max-width: 500px;
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
</style>