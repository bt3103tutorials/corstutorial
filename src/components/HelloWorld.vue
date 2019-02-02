<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h2> Result from AWS Lambda: {{ test }} </h2>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data() {
    return {
      msg: 'Welcome to your Vue.js app',
      test: 'hello, not from lambda',
    };
  },
  mounted: function () {
    this.fetchURL();
  },
  methods: {
    fetchURL: async function () {
      let res = await fetch('https://eoiaxewpyl.execute-api.us-west-2.amazonaws.com/default/corsTutorialWrong');
      // link with CORS header: https://sux8on7u93.execute-api.us-west-2.amazonaws.com/default/corsTutorial
      const json = await res.clone().json();
      this.test = json;
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
