<template>
    <div class="post" @click="favoritePost(post.id)">        
        <h1>@{{username}}</h1>
        <h3>{{post.title}}</h3>
        <p>{{post.content}}</p>
    </div>
</template>

<script>
export default {
    name: 'PostsComponent',
    props: {
        post: {
            type: Object,
            required: true
        },
        username: {
            type: String,
            required: true
        }
    },
    methods: {
        favoritePost(id){
            this.$emit('favorite',id)
        }
    }
}
</script>

<style>
.post{
        background-color: #ffffff;
    margin-left: 40px;
    margin-top: 10px;
    padding: 10px;
    border-radius: 8px;
    box-sizing: border-box;
    transition: all ease-in-out 0.3s;
    cursor: pointer;
}
.post:hover{
    transform: scale(0.9,0.9);
    border:1px solid #dfdfdf;
}
</style>