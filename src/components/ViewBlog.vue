<template>
  <div>
 <h1 @click = "getBlogpost()">Get Blog Post</h1>

 <div class="blog-container" v-for="blogger in bloggers" :key="blogger[1]">
   <h2>{{ blogger[0] }}</h2>
   <p>{{ blogger[2] }}</p>
  <delete-blog :blogid="blogger[2]"></delete-blog>
  <update-blog :blogid="blogger[2]"></update-blog>
   
  </div>
  </div>
</template>

<script>
import axios from 'axios';
import UpdateBlog from "./UpdateBlog.vue";
import DeleteBlog from "./DeleteBlog.vue"
export default {
  data() {
    return{
      bloggers: [],
    };
  },
  components: {
    UpdateBlog,
    DeleteBlog
  },
    methods: {
      getBlogpost: function(){
        axios.request ({
          url: "https://blogpsts.ml/api/bloggers",
          method: "GET"
        })
        .then((response)=> {
          console.log(response)
          this.bloggers = response.data
        })
        .catch((error)=> {
          console.log(error)
        })
      },
    }
}
</script>


<style scoped>
.blog-container {
  max-width: 350px
}
</style>
