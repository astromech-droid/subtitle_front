<template>
  <div class="hello">
    <h1>{{ msg }}</h1>

    <form>
      <input v-on:input="input" v-model="text_input">
    </form>

    <ul v-for="line in lines" v-bind:key="line.line_number">
      <li>{{line._source.text}}</li>
    </ul>

  </div>
</template>

<script>
const axios = require("axios")

export default {
  name: 'SearchLines',
  data: () => {
    return {
      //lines: [{line_number: 1, start:"00:00:00", text: "This is a pen."}, {line_number: 2, start: "00:00:01", text: "Hello world!"}],
      text_input: "",
      lines: []
    }
  },
  props: {
    msg: String
  },
  methods: {
    input(){
      //this.$data.msg = event.target.value
      console.log(this.text_input)
      axios({
        method: "post",
        url: "http://localhost:9200/subtitles/_search",
        auth: {
          username: "elastic",
          password: "aeVIUEp4_aPlkRxxUfA9"
        },
        headers: {
          "Content-Type": "application/json"
        },
        data: JSON.stringify({
          query: {
            match: {
              text: this.text_input
            }
          }
        })

      })
      .then((response)=>{
        let response_data = response.data
        this.lines = response_data.hits.hits
        console.log(response_data.hits.hits)
      })
    }
  }
}
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
