<template>
  <div>
    <h1>Project Twitter Box Client</h1>

    <div class="box">
      <textarea v-model="text" :maxlength="maxChars" />
      <div class="chars-left">{{ charsRemaining }}</div>
      <button @click="addTweet">Submit</button>
    </div>
    <div class="tweets">
      <div v-for="(tweet, idx) in tweets" :key="idx">
        <div class="box">
          {{ tweet }}
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    msg: String,
  },
  data() {
    return {
      text: "",
      maxChars: 280,
      tweets: [],
    };
  },
  methods: {
    addTweet() {
      this.tweets.unshift(this.text);
      this.text = "";
      this.calculateChars();
    },
  },
  computed: {
    charsRemaining() {
      return this.maxChars - this.text.length;
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.box {
  width: 50%;
  background-color: #b8dcdc;
  padding: 1em;
  margin: 0 auto 1em auto;
  display: flex;
  justify-content: center;
  align-items: center;
  box-shadow: 0 20px 25px -5px rgba(0, 0, 0, 0.1),
    0 10px 10px -5px rgba(0, 0, 0, 0.04);
}

.box textarea {
  margin-right: 0.5em;
  height: 4em;
  width: 20em;
}

.chars-left {
  font-size: 0.8em;
}

button {
  margin-left: 10px;
}
</style>
