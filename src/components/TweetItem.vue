<template>
  <div class="tweet-item" @click="favouriteTweet(tweet.id)">
      <div class="user-profile_tweet">
          <div class="tweet-item_user">
              @{{ username }}
          </div>
          <div class="tweet-item_content">
              {{ tweet.content }}
          </div>
      </div>
  </div>
</template>

<script>
export default {
    name: "TweetItem",
    props: {
        username: {
            type: String,
            required: true
        },
        tweet: {
            type: Object,
            required: true
        }
    },
    methods: {
        favouriteTweet(id) {
            this.$emit('favorite', id);
        }
    }
};
</script>

<style>
.tweet-item {
    padding: 20px;
    background-color: white;
    border-radius: 5px;
    border: 1px solid #dfe3e8;
    box-sizing: border-box;
    cursor: pointer;
    transition: all 0.25s ease;
}

.tweet-item:hover {
    transform: scale(1.1, 1.1);
}

.tweet-item_user {
    font-weight: bold;
}
</style>