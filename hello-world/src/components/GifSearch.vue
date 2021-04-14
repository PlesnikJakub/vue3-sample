<template>
  <div class="hello">
    <input v-model="searchQuery" placeholder="Type something" />
    <br/>
    <strong>{{ searchIndicator }}</strong>
    <div v-if="searchResult">
          <GifCollection  v-bind:collection="searchResult"/>
    </div>
  </div>
</template>

<script>
import GifCollection from './GifCollection';
var _ = require('lodash')
export default {
  name: "GifSearch",
  components: {
    GifCollection
  },
  data() {
    return {
      searchQuery: "",
      searchQueryIsDirty: false,
      isCalculating: false,
      searchResult: []
    };
  },
  computed: {
    searchIndicator: function() {
      if (this.isCalculating) {
        return "⟳ Fetching new results";
      } else if (this.searchQueryIsDirty) {
        return "... Typing";
      } else {
        return "✓ Done";
      }
    },
  },
  watch: {
    searchQuery: function() {
      this.searchQueryIsDirty = true;
      this.expensiveOperation();
    },
  },
  methods: {
    // This is where the debounce actually belongs.
    expensiveOperation: _.debounce(function() {
      this.isCalculating = true;
      setTimeout(
        function() {

          const api_key = process.env.VUE_APP_GIPGY_API_KEY;

          fetch(`https://api.giphy.com/v1/gifs/search?api_key=${api_key}&q=${this.searchQuery}&limit=25&offset=0&rating=g&lang=en`, {
            method: 'get',
            headers: {
              'content-type': 'application/json'
            }
          })
          .then(response => response.json())
          .then(data => this.searchResult = data.data);

          this.isCalculating = false;
          this.searchQueryIsDirty = false;
        }.bind(this),
        1000
      );
    }, 500),
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
