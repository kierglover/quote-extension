<template>
     <div class="container">
          <!-- <h2>{{hello}}</h2> -->
          <div class="card">
               <div class="card__body">
                    {{quotes.quote}}
               </div>
          </div>
     </div>
</template>

<script>
import axios from 'axios';
export default {
     name: 'Hello',
     data() {
          return {
               quotes: [],
               hello: 'Hello World!',
               testQuote: 'This is a test quote. Test test test test test test test test'
          };
     },
     mounted() {
          axios.get("http://quotes.stormconsultancy.co.uk/random.json")
          .then(response => {this.quotes = response.data})
     },
};
</script>
