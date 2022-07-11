<template>
    <div class="post">        
        <h1>@{{username}}</h1>
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
}
.post:hover{
    transform: scale(0.9,0.9);
    border:1px solid #dfdfdf;
}
</style>