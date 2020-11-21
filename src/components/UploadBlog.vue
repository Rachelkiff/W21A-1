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
                        bloggerUsername: this.bloggerUsername,
                        bloggerContent: this.bloggerContent,
                        bloggerCreatedat: this.bloggerCreatedat
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