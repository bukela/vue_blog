<template>
  <div id="app">
    <!-- <add-blog v-bind:boo="boo"></add-blog> -->
    <show-blogs></show-blogs>
  </div>
</template>

<script>
import addBlog from './components/addBlog.vue';
import showBlogs from './components/showBlogs.vue';
export default {
  components: {
    'add-blog': addBlog,
    'show-blogs': showBlogs
  },
  data () {
    return {
      boo: 'ZDRAVOOOOOOO'
    }
  }
}
</script>

<style>
body {
  margin: 0;
  background-color: rgb(238, 238, 238);
  font-family: Arial, Helvetica, sans-serif;
}
</style>
