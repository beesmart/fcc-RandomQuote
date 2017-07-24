

<template>

  <div class="quote container">
     <h2>Random Quote Generator <span class="label label-default">Built with Vue.js</span></h2>
       	 <hr />
        <div class="myQuote">
          <div v-if="posts && posts.length">
            <div v-for="post of posts">
              <h4 v-html="post.content"></h4>
              <div class="row">
                <span class="glyphicon glyphicon-user" aria-hidden="true"></span>
                <p class="quote-title" v-html="post.title"></p>
              </div>
            </div>
          </div>

        </div>
        <hr />
        <div class="row">
          <div class="col-lg-6 col-md-6">
            <button v-on:click="getQuote" id="get_quote_btn" class="btn button btn-primary">Get New Quote</button>
          </div>
          <div class="col-lg-6 col-md-6">
            <a v-bind:href="finalUrl" title="Tweet this quote!">
            <button class="btn" id="tweet_quote_btn">
                 <i class="fa fa-twitter"></i>
            </button>
             </a>

          </div>
        </div>


  </div>
</template>

<script>
var axios = require('axios')

export default {
  name: 'quote',
  data () {
    return {
      posts: null,
      title: this.title,
      content: this.content,
      url: "https://twitter.com/intent/tweet?text=",
      finalUrl: ""
    }
  },
  methods: {
    getQuote: function () {
      axios.get('https://quotesondesign.com/wp-json/posts?filter[orderby]=rand&filter[posts_per_page]=1')
      .then((response) => {
        console.log(response)
        this.posts = response.data
        this.quote = this.posts[0].content.replace(/(<([^>]+)>)/ig, '');
        this.title = this.posts[0].title

        this.tweetReadyString = encodeURI(this.quote + ' - ' + this.title)
        this.finalUrl = this.url + this.tweetReadyString
      })
      .catch((error) => {
        console.log(error.message)
        this.posts = [];
      })
    }
  },


  mounted: function () {
    this.getQuote()
  }
}
</script>
