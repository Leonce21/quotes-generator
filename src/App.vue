<template>
  <div class="app">
    <AppHeader title="The anime Quote"/>
    <AppQuote :quote="quote"/>
    <div class="btn-container">
      <button @click="getQuote">Generate</button>
    </div>

    <QuoteList :quotes="quotes"/>
  </div>
  
</template>

<script>
import AppHeader from './components/AppHeader.vue'
import AppQuote from './components/AppQuote.vue'
import QuoteList from './components/QuoteList.vue'



export default {
  name: 'App',

  components: {
    AppHeader,
    AppQuote,
    QuoteList
  },

  data(){
    return{
      quote: {
        content: 'content goes here',
        anime: 'Naruto',
        character: 'Madara'
      },
      quotes:[]
    }
  },
  methods: {
    async getQuote(){
      if(this.quote.content){
        this.quotes = [...this.quotes, this.quote]
      }

      const data = await fetch('api/quotes').then(res => res.json());

      this.quote = {
        content: data.quote,
        anime: data.anime,
        character: data.character
      }
    }
  },
  created(){
    this.getQuote();
  }

}
</script>

<style lang="scss">
*{
  padding:0;
  margin:0;
  box-sizing:border-box;
  font-family: 'Fira Sans', sans-serif;
}
:root{
  --primary: #D81E5B;
  --secondary: #8A4FFF;
  --tertiary: #32CBFF;
  --dark: #131A26;
  --light: #EEE;
  --grey: #848484;
}

.btn-container{
  display: flex;
  justify-content: center;
  padding: 0px 32px;
  margin: 64px auto;

  button{
    border:none;
    outline: none;
    background-color: var(--primary);
    padding: 16px 32px;
    border-radius: 99px;
    color: var(--light);
    font-size: 28px;
    font-weight: 700;
    text-transform: uppercase;
    cursor: pointer;
    transition: 0.4s;

    &:hover{
      background-color: var(--secondary);
    }
  }
}
</style>
