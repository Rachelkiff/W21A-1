<template>
  <div id="app">
    <view-blog></view-blog>
    <upload-blog></upload-blog>
  </div>
</template>

<script>

import ViewBlog from './components/ViewBlog.vue';
import UploadBlog from './components/UploadBlog.vue'
export default {
  name: "App",
      
  components: 
    ViewBlog,
    UploadBlog 
  }

</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
