<template>
  <div class="userProfileJHA">
    <div class="nameSectionJHA">
        <div class="usernameJHA">
            <h1>@{{ user.username }}</h1>
        </div>
        <div class="badge" v-if="user.isAdmin">
          Admin
        </div>
        <div class="followersCountJHA">
            <p><strong> Followers :</strong> {{user.followers}}</p>
        </div>
    </div>
<div class="post-wrapper">
  <PostsComponent v-for='post in user.posts' :username="user.username" :post="post" :key="post.id"/>

  </div>
  </div>
</template>

<script>
import PostsComponent from './PostsComponent.vue';
export default {
    name: "UserProfile",
    data() {
        return {
            user: {
                id: 1,
                name: "Junaid Hussnain",
                username: "_JunaidHussnain",
                email: "junaidhussnain369@gmail.com",
                followers: 0,
                isAdmin: true,
                posts: [
                    { id: 1, content: "Lorem ipsum dolor sit amet, consectetur adipisicing elit. Vel temporibus esse quos id maxime quis, tempora, officia quidem, enim dolore ipsum! Natus in quaerat labore voluptatibus tempora repudiandae, iure aliquam." },
                    { id: 2, content: "Lorem ipsum dolor sit amet, consectetur adipisicing elit. Vel temporibus esse quos id maxime quis, tempora, officia quidem, enim dolore ipsum! Natus in quaerat labore voluptatibus tempora repudiandae, iure aliquam." },
                    { id: 3, content: "Lorem ipsum dolor sit amet, consectetur adipisicing elit. Vel temporibus esse quos id maxime quis, tempora, officia quidem, enim dolore ipsum! Natus in quaerat labore voluptatibus tempora repudiandae, iure aliquam." },
                    { id: 4, content: "Lorem ipsum dolor sit amet, consectetur adipisicing elit. Vel temporibus esse quos id maxime quis, tempora, officia quidem, enim dolore ipsum! Natus in quaerat labore voluptatibus tempora repudiandae, iure aliquam." },
                    { id: 5, content: "Lorem ipsum dolor sit amet, consectetur adipisicing elit. Vel temporibus esse quos id maxime quis, tempora, officia quidem, enim dolore ipsum! Natus in quaerat labore voluptatibus tempora repudiandae, iure aliquam." },
                    { id: 6, content: "Lorem ipsum dolor sit amet, consectetur adipisicing elit. Vel temporibus esse quos id maxime quis, tempora, officia quidem, enim dolore ipsum! Natus in quaerat labore voluptatibus tempora repudiandae, iure aliquam." }
                ]
            },
        };
    },
    methods: {
        followUser() {
            this.user.followers++;
        }
    },
    mounted() {
        this.followUser();
    },
    components: { PostsComponent }
};
</script>

<style>
h1{
    font-size:large;
}
.userProfileJHA {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  display: flex;
  max-height:300px
}
.nameSectionJHA{
  padding: 20px;
  background-color: #ffffff;
  border-radius: 5px;
  display: flex;
  flex-direction: column;
}
.badge{
  margin-right: auto;
  padding: 0 10px;
  background-color: mediumslateblue;
  color: #ffffff;
  border-radius: 5px;
}

</style>
