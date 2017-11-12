<template>
  <div id="app">
    <h1>在线翻译</h1>
    <h5 class="text-muted">简单 / 易用 / 便捷</h5>
    <translateForm v-on:formSub="translateText"></translateForm>
    <translateOutput v-text="translatedText"></translateOutput>
  </div>
</template>

<script>

import TranslateForm from './components/TranslateForm'
import TranslateOutput from './components/TranslateOutput'

export default {
  name: 'app',
  data() {
    return{
      translatedText:""
    }
  },
  methods: {
    translateText(text,language) {
      // alert(text);
      this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20171102T132745Z.4012053db8c5b673.d6468625d553a1c2c729ac9083fb4acfb9841097&lang='+language+'&text='+text).then((response)=>{
        // console.log(response);
        this.translatedText = response.body.text[0];
      })
    }
  },
  components: {
    TranslateForm,
    TranslateOutput
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
