<template>
  <div>
    <p>Edit your blog post</p>
    <input v-model="bloggerUsername" type="text" />
    <p>Blog</p>
    <textarea v-model="bloggerContent"></textarea>
    
    <button @click="updateBlog()">Submit</button>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "UpdateBlog",
  data() {
    return {
      bloggerUsername: "",
      bloggerContent: "",
    
    };
  },
  props: {
    bloggerid: {
      type: Number,
      required: true,
    },
  },
  methods: {
    updateBlog: function () {
      axios
        .request({
          url: "http://127.0.0.1:5000/api/bloggers",
          method: "PATCH",
          headers: {
            "Content-Type": "application/json",
          },
          data: {
            bloggerUsername: this.bloggerUsername,
            bloggerContent: this.bloggerContent,
            id: this.bloggerId
          },
        })
        .then((response) => {
            console.log(response)
        })
        .catch((error) => {
            console.log(error)
        });
    },
  },
};
</script>

<style scoped>
</style>