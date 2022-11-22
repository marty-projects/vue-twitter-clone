<template>
<div class="user-profile">
  <div class="user-profile__user-panel">
  <h1 class="user-profile__username">@{{ user.username }}</h1>
  <div class="user-profile__admin-badge" v-if="user.isAdmin">
      Admin
  </div>
  <div class="user-profile__follower-count">
    <strong>Followers: </strong> {{followers}}
    </div>
  </div>
  <div class="user-profile__posts-wrapper">
      <PostItem 
      v-for="post in user.posts" 
      :key="post.id" 
      :username="user.username" 
      :post="post" 
      @favorite="toggleFavorite"
      />
 </div>
  </div>
</template>

<script>
import PostItem from "./PostItem.vue";

export default {

  name: "UserProfile",
  components: {PostItem},
  data() { 
    return {
      followers: 0,
      user: {
        id: 1,
        username: '_ben',
        firstname: 'Benjamin',
        lastname: 'Smith',
        email: 'ben@gmail.com',
        isAdmin: true,
        posts: [
            {
                id: 1,
                content: 'What an app!',
            },
             {
                id: 2,
                content: 'Thanks for the tutorial, Mitch!',
            }
            ]
        }  
      }
    },
    watch: {
      followers(newFollowerCount, oldFollowerCount) {
        if (oldFollowerCount < newFollowerCount) {
          console.log(`${this.user.username} has gained a follower!`)
        }
      }
    },

    computed: {
      fullName() {
        return `${this.user.firstname} ${this.user.lastname}`;
      }
    },

    methods: {
      followUser()
          {  this.followers++; 
      },

      toggleFavourite(id) {
          console.log(`Favorited Post #${id}`)
      }
  },
  mounted() {
    this.followUser();
  }
  }
</script>

<style>
.user-profile {
    display: grid;
    grid-template-columns: 1fr 3fr;
    width: 100%;
    padding: 50px 5%;
}

.user-profile__user-panel {
    display:flex;
    flex-direction: column;
    margin-right: 50px;
    padding: 20px;
    background-color: gray;
    border-radius: 5px;
    border: 1px solid #DFE3E8;
}

h1 {
    margin: 0;
}

.user-profile__admin-badge {
    background: orange;
    color: white;
    border-radius: 5px;
    margin-right: auto;
    padding: 0 10px; 
    font-weight: bold;
}

</style>