<template>
  <div class="user-profile">
      <div class="user-profile_user-panel">
        <h1 class="user-profile_username">{{ user.username }}</h1>
        <div class="user-profile_admin-badge" v-if="user.isAdmin">
            Admin
        </div>
        <div class="user-profile_follower-count">
            <strong>Followers: </strong> {{ followers }}
        </div>
      </div>    
      <div class="user-profile_tweets-wrapper">
            <TweetItem  v-for="tweet in user.tweets" :key="tweet.id" :username="user.username" :tweet="tweet"/> 
      </div>
  </div>
</template>

<script>
import TweetItem from './TweetItem';


export default {
    name: "UserProfile",
    components: { TweetItem },
    data() {
        return {
        isLoading: false,
        followers: 0,
        user: {
            id: 1,
            username: 'Test',
            firstName: 'John',
            lastName: 'Doe',
            email: 'joemari.supan18@gmail.com',
            isAdmin: true,
            tweets: [
                {id: 1, content: "Twitter is awesome"},
                {id: 2, content: "Don't forget to surview"}
            ]
        }
    }
  },
  watch: {
    followers(newFollowCount, oldFollowCount) {
      if(oldFollowCount < newFollowCount) {
        console.log(`${this.user.username} has gane a follower`);
      }
    }
  },
  computed: {
    fullName() {
      return `${this.user.firstName} ${this.user.lastName}`;
    }
  },
  methods: { 
    followUser() {
      this.followers++;
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

.user-profile_user-panel {
    display: flex;
    flex-direction: column;
    margin-right: 50px;
    padding: 20px;
    background-color: white;
    border-radius: 5px;
    border: 1px solid #Dfe3e8;
}

.user-profile_admin-badge {
    background: rebeccapurple;
    color: white;
    border-radius: 5px;
    margin-right: auto;
    padding: 0 10px;
    font-weight: bold;
}

h1 {
    margin: 0;
}

</style>