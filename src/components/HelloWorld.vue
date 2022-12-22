<template>
  <div>
    <h1>Project Twitter Box Client</h1>

    <form v-on:submit.prevent class="box">
      <textarea
      v-model.trim="tweet"
      v-bind:maxlength="characters"
      type="text" 
      />
      <button 
      v-show="tweet.length > 0"
      @click="addTweet"
      :disabled="!maxC"
      >
      Submit
      </button>
    </form>
    <h4 :class="{ 'red' : !maxC}">
      characters remaining {{ maxC }}
    </h4>
    <div :class="{'tweet' : tweet.length > 0}" v-for="(tweet, index) in tweets" v-bind:key="index">
      <h4>{{ tweet }}</h4>
      <button v-if="tweet.length > 0" @click="removeTweet(index)">delete</button>
    </div>
  </div>
</template>




<script>
export default {
  name: "HelloWorld",
  data() {
    return {
      maxCharacters: '',
      characters: 40,
      tweets: [],
      tweet: ''
    }
  },
  methods: {
    addTweet() {
      this.tweets.push(this.tweet)
      this.tweet = ''
    },
    removeTweet(index) {
      this.tweets.splice(index, 1)
    }
  },
  computed: {
    maxC() {
      return this.characters - this.tweet.length
    },

  }
}
</script>





<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.box {
  width: 33%;
  background-color: #b8dcdc;
  height: 100px;
  margin: 0 auto;
  display: flex;
  justify-content: center;
  align-items: center;
  box-shadow: 0 20px 25px -5px rgba(0, 0, 0, 0.1),
    0 10px 10px -5px rgba(0, 0, 0, 0.04);
}
.red {
  color: red;
}

.tweet {
  width: 30%;
  background-color: #b8dcdc;
  margin: auto;
  padding: 20px 15px;
  margin-top: 10px;
  box-shadow: 0 20px 25px -5px rgba(0, 0, 0, 0.1),
      0 10px 10px -5px rgba(0, 0, 0, 0.04);
}

button {
  margin-left: 10px;
  padding: 10px 15px;
  border: none;
  color: white;
  cursor: pointer;
  background-color: rgb(66, 154, 248);
}
</style>