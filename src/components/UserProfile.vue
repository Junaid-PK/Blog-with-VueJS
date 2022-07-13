<template>
  <div class="userProfileJHA">
    <div class="nameSectionJHA">
      <div class="usernameJHA">
        <h1>@{{ user.username }}</h1>
      </div>
      <div class="badge" v-if="user.isAdmin">Admin</div>
      <div class="followersCountJHA">
        <p><strong> Followers :</strong> {{ user.followers }}</p>
        <p><strong> Total Posts :</strong> {{ user.posts.length }}</p>
      </div>
    </div>
    <div class="post-wrapper">
      <PostsComponent
        v-for="post in user.posts"
        :username="user.username"
        :post="post"
        :key="post.id"
        @favorite="togglefavorite"
      />
    </div>
  </div>
  <button class="button" @click="isActive = true">Add New</button>
  <ModalComponent :toggle="isActive" @save="savePost" @close="isActive = !isActive">
    <div class="mb-3">
        Add a New Post
    </div>
    <hr>
    <div class="mb-3">
      <label for="exampleFormControlInput1" class="form-label"
        >Post Title</label
      >
      <input
        type="text"
        class="form-control"
        id="exampleFormControlInput1"
        v-model="newTitle"
      />
    </div>
    <div class="mb-3">
      <label for="exampleFormControlTextarea1" class="form-label"
        >Description</label
      >
      <textarea
        class="form-control"
        id="exampleFormControlTextarea1"
        rows="3"
        v-model="newContent"
      ></textarea>
    </div>
  </ModalComponent>
</template>

<script>
import PostsComponent from "./PostsComponent.vue";
import ModalComponent from "./ModalComponent.vue";
import { ref } from "vue";
export default {
  name: "UserProfile",
  setup() {
    const isActive = ref(false);
    return { isActive };
  },
  data() {
    return {
        newTitle:'',
        newContent:'',
      user: {
        id: 1,
        name: "Junaid Hussnain",
        username: "_JunaidHussnain",
        email: "junaidhussnain369@gmail.com",
        followers: 0,
        isAdmin: true,
        posts: [
          {
              id: 1,
            title: "Why is Vue Js Awesome?",
            content:
              "Lorem ipsum dolor sit amet, consectetur adipisicing elit. Vel temporibus esse quos id maxime quis, tempora, officia quidem, enim dolore ipsum! Natus in quaerat labore voluptatibus tempora repudiandae, iure aliquam.",
          },
        ],
      },
    };
  },
  methods: {
    followUser() {
        this.user.followers++;
    },
    togglefavorite(id) {
        alert(`Post Number ${id} is favorited`);
    },
    savePost(){
        if(this.newTitle && this.newContent){
            this.user.posts.unshift(
                {
                    id: this.user.posts.length + 1,
                    title: this.newTitle,
                    content: this.newContent
                }
            );
            this.newTitle='';
            this.newContent='';
        }
    }
  },
  mounted() {
      this.followUser();
  },
  components: { PostsComponent, ModalComponent },
};
</script>

<style>
h1 {
  font-size: large;
}
.userProfileJHA {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  display: flex;
  max-height: 300px;
}
.nameSectionJHA {
  padding: 20px;
  background-color: #ffffff;
  border-radius: 5px;
  display: flex;
  flex-direction: column;
}
.badge {
  margin-right: auto;
  padding: 0 10px;
  background-color: mediumslateblue;
  color: #ffffff;
  border-radius: 5px;
}

@media only screen and (min-width: 600px) {
  body {
    justify-content: center;
    align-items: center;
    display: flex;
    height: 100vh;
    font-size: 100%;
  }
}

.button {
  -webkit-appearance: none;
  -moz-appearance: none;
  appearance: none;
  background: #16a34a;
  border-radius: 0.25em;
  color: white;
  cursor: pointer;
  display: inline-block;
  font-weight: 500;
  height: 3em;
  line-height: 3em;
  padding: 0 1em;
}
.button:hover {
  background-color: #17ac4e;
}

.details-modal {
  background: #ffffff;
  border-radius: 0.5em;
  box-shadow: 0 10px 20px rgba(0, 0, 0, 0.2);
  left: 50%;
  max-width: 90%;
  pointer-events: none;
  position: absolute;
  top: 50%;
  transform: translate(-50%, -50%);
  width: 30em;
  text-align: left;
  max-height: 90vh;
  display: flex;
  flex-direction: column;
}
.details-modal .details-modal-title {
  color: #111827;
  padding: 1.5em 2em;
  pointer-events: all;
  position: relative;
  width: calc(100% - 4.5em);
}
.details-modal .details-modal-title h1 {
  font-size: 1.25rem;
  font-weight: 600;
  line-height: normal;
}
.details-modal .details-modal-content {
  border-top: 1px solid #e0e0e0;
  padding: 2em;
  /* pointer-events: all; */
  overflow: auto;
}

.details-modal-overlay {
  transition: opacity 0.2s ease-out;
  pointer-events: none;
  background: rgba(15, 23, 42, 0.8);
  position: fixed;
  opacity: 0;
  bottom: 0;
  right: 0;
  left: 0;
  top: 0;
}
.container {
  text-align: center;
  max-width: 40em;
  padding: 2em;
  transition: ease-in all 0.5s;
}
.container > h1 {
  font-weight: 700;
  font-size: 2rem;
  line-height: normal;
  color: #111827;
}
.container > p {
  margin-top: 2em;
  margin-bottom: 2em;
}
.container sup {
  font-size: 1rem;
  margin-left: 0.25em;
  opacity: 0.5;
  position: relative;
}
</style>
