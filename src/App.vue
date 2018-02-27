<template>
  <div id="app">
    <add-blog v-bind:boo="boo"></add-blog>
  </div>
</template>

<script>
import addBlog from './components/addBlog.vue';
export default {
  components: {
    'add-blog': addBlog
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
  background-color: aquamarine;
}
</style>
