<template>
  <div>
    <button @click="deleteBlog()">Delete</button>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "DeleteBlog",

  props: {
    bloggerid: {
      type: Number,
      required: true,
    },
  },
  methods: {
    deleteBlog: function () {
      axios
        .request({
          url: "http://127.0.0.1:5000/api/bloggers",
          method: "Delete",
          headers: {
            "Content-Type": "application/json",
          },
          data: {
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