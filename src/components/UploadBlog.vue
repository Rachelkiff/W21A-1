<template>
    <div>
     <p>User Name</p>
     <input v-model="bloggerUsername" type="text">
     <p>Enter your blog post</p> 
     <textarea v-model="bloggerContent"></textarea>
     <p>New blog post</p>
     <button @click="uploadBlog">Submit</button>
     <p>Created at</p>
     <input type="date" v-model="createdAt">

    </div>
</template>

<script>
import axios from "axios"
    export default {
        
        data() {
            return {
                bloggerUsername: "",
                bloggerContent: "",
                createdAt: ""
                
            }
        },
        methods: {
           uploadBlog: function() {
                axios.request({
                    url: "http://127.0.0.1:5000/api/bloggers",
                    method: "POST",
                    headers: {
                        "Content-Type": "application/json"
                    },
                    data: {
                        username: this.bloggerUsername,
                        content: this.bloggerContent,
                        createdAt: this.createdAt
                    }
                }).then((response)=>{
                    console.log(response)
                }).catch((error)=>{
                    console.log(error)
                })
           }
        },
    }
</script>

<style scoped>

</style>