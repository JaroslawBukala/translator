<template>
  <div class="text-center " id="app">
    <h1>Word Translator</h1>
    <h5>Powered by Vue.js</h5>
    <TranslateForm  v-on:formSubmit='translateText'></TranslateForm>
    <TranslateOutput v-text="translatedText"></TranslateOutput>
  </div>
</template>

<script>
import TranslateForm from './components/TranslateForm'
import TranslateOutput from './components/TranslateOutput'
export default {
  name: 'App',
  components:{
    TranslateForm,
    TranslateOutput
  },
  data: function(){
    return{
      translatedText: ''
    }
  },
  methods:{
    translateText: function(text, language){
        this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20190404T220247Z.32e82cbd2f728e73.d08c9c8633b9b49dc9381a5c1f96a1a78f68bdc3&lang='+language+'&text='+text).then((response)=>{
        this.translatedText=response.body.text[0];
        })
    }
  }
}
</script>

<style>
body{
      background:#fefefe
    }
</style>
