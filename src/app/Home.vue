<template>
    <div class="container">
      <div class="card">
        <div class="card__body">
          <p class="card__body__quote">"</p>
          <p>{{quotes.quote}}</p>
          <p class="card__body--light">{{quotes.author}}</p>
        </div>
      </div>
      <div class="footer">
        <div class="footer__body">
          <p class="footer__body__link">{{currentTime}}</p>
        </div>
      </div>
    </div>
</template>

<script>
import axios from "axios";
var moment = require('moment');
export default {
  name: "Hello",
  data() {
    return {
      moment:moment,
      quotes: [],
      currentTime: null,
      hello: "Hello World!",
      testQuote: "This is a test quote. Test test test test test test test test"
    };
  },
  methods: {
    updateCurrentTime() {
      this.currentTime = moment().format('LTS');
    }
  },
  created() {
    this.currentTime = moment().format('LTS');
    setInterval(() => this.updateCurrentTime(), 1 * 1000);
  },
  mounted() {
    axios
      .get("http://quotes.stormconsultancy.co.uk/random.json")
      .then(response => {
        this.quotes = response.data;
      });
  }
};
</script>
