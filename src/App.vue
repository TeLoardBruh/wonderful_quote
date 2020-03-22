<template>
  <div class="container">
    <app-header :quoteCount="quotes.length" :maxQuote="maxQuote"></app-header>
    <app-new-quote @addQuote="newQuote"></app-new-quote>
    <app-quote-grid :quotes="quotes" @deletedQuote="deleteQuote"></app-quote-grid>
    <div class="col-sm-12 text-center">
      <div class="alert alert-info">Info: Click on the quote to delete it.</div>
    </div>
  </div>
</template>

<script>
import QuoteGrid from "./components/QuoteGrid.vue";
import newQuoteVue from "./components/newQuote.vue";
import HeaderApp from "./components/Header.vue";

export default {
  data: function() {
    return {
      quotes: ["Just a wonderful quote"],
      maxQuote: 10
    };
  },
  methods: {
    newQuote(quote) {
      if (this.quotes.length >= this.maxQuote) {
        return alert("Please delete Quotes first!");
      }
      this.quotes.push(quote);
    },
    deleteQuote(index) {
      this.quotes.splice(index, 1);
    }
  },
  components: {
    appQuoteGrid: QuoteGrid,
    appNewQuote: newQuoteVue,
    appHeader: HeaderApp
  }
};
</script>

<style>
</style>
