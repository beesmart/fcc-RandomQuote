<template>
  <div id="app">
    <Quote :cite="quote.cite">
      {{ quote.body }}
    </Quote>
    <div class="col-lg-6 col-md-6">
      <button @click="getQuote()" class="btn button btn-primary">Get New Quote</button>
    </div>
    <div class="col-lg-6 col-md-6">
      <button class="btn" id="tweet_quote_btn">
       <a id="tweet_quote" title="Tweet this quote!">
          <i class="fa fa-twitter"></i>
       </a>
      </button>
    </div>

  </div>
</template>





<script>
import Quote from '@/components/Quote'

var axios = require('axios')

export default {
  name: 'App',
  components: {
    Quote
  },
  data() {
		return {
			quote: {
				body: '',
				cite: '',
			},
			loading: true
		};
	},
  methods: {
    getQuote() {
      this.loading = true;
      axios.get('https://quotesondesign.com/wp-json/posts?filter[orderby]=rand&filter[posts_per_page]=1')
      .then((response) => {
        console.log(response)
        this.quote.body = response.data[0].content;
				this.quote.cite = response.data[0].title;
        this.loading = false;
        console.log(response.data[0].content)
      })
      .catch((error) => {
        console.log(error.message)
        this.loading = false;
      })
    }
  },
  mounted() {
		this.getQuote();
	}
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
