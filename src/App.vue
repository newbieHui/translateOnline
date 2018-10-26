<template>
  <div id="app">
    <img src="./assets/logo.png">
    <HelloWorld></HelloWorld>
    <TranslateInput v-on:formSubmit="textTranslate"></TranslateInput>
    <TranslateOutput v-bind:outputText="translatedText"></TranslateOutput>
    <PageFooter></PageFooter>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld'
import TranslateInput from './components/TranslateInput.vue'
import TranslateOutput from './components/TranslateOutput.vue'
import PageFooter from './components/PageFooter.vue'
import md5 from 'blueimp-md5'
import $ from 'jquery'

export default {
  name: 'App',
  components: {
    HelloWorld,
    TranslateInput,
    TranslateOutput,
    PageFooter,
  },
  data:function(){
      return {
        appKey: '47bb6e424790df89',
        key: 'NH2VxBadIlKlT2b2qjxaSu221dSC78Ew',
        salt: (new Date()).getTime(),
        from: '',
        to: '',
        translatedText:''
      }
  },
  methods: {
    textTranslate: function (text,translateLanguage) {
        if(text==''){
            alert('请先输入需要翻译的文本');
        }else{
          let vm = this;
          $.ajax({
            url: 'http://openapi.youdao.com/api',
            type: 'post',
            dataType: 'jsonp',
            data: {
              q: text,
              appKey: this.appKey,
              salt: this.salt,
              from: this.from,
              to: translateLanguage,
              sign: md5(this.appKey + text + this.salt + this.key)
            },
            success: function (data) {
              vm.$set(vm.$data, 'translatedText', data.translation[0])
            }
          })
        }
    }
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
