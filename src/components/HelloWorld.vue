<template>
  <div>
    <h1>Project Twitter Box Client</h1>

    <div class="box">
      <textarea v-model="text" @input="checkLength" />
      <div class="chars-left">{{ charsRemaining }}</div>
      <button>Submit</button>
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
    };
  },
  methods: {
    checkLength() {
      if (this.text.length >= this.maxChars) {
        this.text = this.text.substring(0, this.maxChars);
      }
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

.box textarea {
  margin-right: 0.5em;
}

.chars-left {
  font-size: 0.8em;
}

button {
  margin-left: 10px;
}
</style>
