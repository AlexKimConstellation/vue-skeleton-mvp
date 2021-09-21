<template>
  <div>
    <v-flex class="quote" xs12 text-xs-center mt-5 mb-5>
      {{ this.quote }}
      <br />
      <br />
      <button class="bmc-button" v-on:click="getChuckNorrisQuote()">
        <span style="margin-left: 5px">{{ $t('landing.BUTTON') }}</span>
      </button>
    </v-flex>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  data() {
    return {
      quote: '',
      errors: []
    }
  },

  methods: {
    // get Chuck Norris quote
    getChuckNorrisQuote() {
      axios
        .get(`https://api.chucknorris.io/jokes/random`)
        .then((response) => {
          // JSON responses are automatically parsed.
          console.log(response.data)
          this.quote = response.data.value
        })
        .catch((e) => {
          this.errors.push(e)
        })
    },

    // get inspirational quote
    getDadJoke() {
      axios
        .get(`https://icanhazdadjoke.com/`, { Accept: 'application/json' })
        .then((response) => {
          // JSON responses are automatically parsed.
          console.log(response.data)
          this.quote = response.data.value
        })
        .catch((e) => {
          this.errors.push(e)
        })
    }
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css?family=Cookie');

.bmc-button img {
  width: 27px !important;
  margin-bottom: 1px !important;
  box-shadow: none !important;
  border: none !important;
  vertical-align: middle !important;
}
.bmc-button {
  line-height: 36px !important;
  height: 37px !important;
  text-decoration: none !important;
  display: inline-flex !important;
  color: #ffffff !important;
  background-color: #ff813f !important;
  border-radius: 3px !important;
  border: 1px solid transparent !important;
  padding: 1px 9px !important;
  font-size: 40px !important;
  letter-spacing: 0.6px !important;
  margin: 0 auto !important;
  font-family: 'calibri' !important;
  -webkit-box-sizing: border-box !important;
  box-sizing: border-box !important;
  -o-transition: 0.3s all linear !important;
  -webkit-transition: 0.3s all linear !important;
  -moz-transition: 0.3s all linear !important;
  -ms-transition: 0.3s all linear !important;
  transition: 0.3s all linear !important;
}

.quote {
  font-size: 40px !important;
  font-style: italic;
}
</style>
