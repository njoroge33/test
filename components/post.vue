<template>
    <h1>Posts</h1>
    <div v-for="post in posts" :key="post.id" class="border border-2">
    <p>{{ post.title }}</p>
    <br>
    <p>{{ post.content }}</p><br>

    </div>
    </template>
    
    <script setup lang="ts">
    
    const posts = ref([]);
    
    async function getPosts() {
        const post_end= "https://sample-api.gojjoapps.com/api/posts/posts/"
        await useFetch (post_end, {
            method: 'GET',
            headers: {
            Authorization: 'Token 439e871c1f6e90a4509b026191ff6ea00a7ec005',
            },
        }).then(response=>{
            console.log(response.status.value)
            console.log(response.data.value)
            if(response.status.value==="success"){
                posts.value = response.data.value;
                console.log(posts)
            }
        })
    }
    
    onMounted(()=>{
        getPosts()
    })
        
    
    </script>