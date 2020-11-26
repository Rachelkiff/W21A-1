<template>
    <div>
     <p>User Name</p>
     <input v-model="bloggerUsername" type="text">
     <p>Enter yur blog post</p> 
     <textarea v-model="bloggerContent"></textarea>
     <p>New blog post created</p>
     <input v-model="bloggerCreatedat" type="text">
     <button @click="uploadBlog">Submit</button>

    </div>
</template>

<script>
import axios from "axios"
    export default {
        name: "UploadBlog",
        data() {
            return {
                bloggerUsername: "",
                bloggerContent: "",
                bloggerCreatedat :"",
            }
        },
        methods: {
           uploadBlog: function() {
                axios.request({
                    url: "https://blogpsts.ml/api/bloggers",
                    method: "POST",
                    headers: {
                        "Content-Type": "application/json"
                    },
                    data: {
                        username: this.bloggerUsername,
                        content: this.bloggerContent,
                        createdat: this.bloggerCreatedat
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