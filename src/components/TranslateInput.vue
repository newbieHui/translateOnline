<template>
  <div>
    <form v-on:submit.prevent="formSubmit">
      <div>
        <!--<input type="text" v-model="text" placeholder="请输入需要翻译的文本">-->
        <textarea v-model="text" placeholder="请输入需要翻译的文本"></textarea>
      </div>
      <div class="secondInput">
        <select class="select" v-model="translateLanguage">
          <option value="en">英语</option>
          <option value="ko">韩语</option>
          <option value="ru">俄语</option>
        </select>
        <div class="submitButton">
          <input class="button" type="submit" value="翻译">
        </div>
      </div>
    </form>
  </div>
</template>

<script>
  export default{
    name:'TranslateInput',
    data(){
        return{
          text:'',
          translateLanguage:'en'
        }
    },
    methods:{
        formSubmit:function(){
            this.$emit('formSubmit',this.text,this.translateLanguage);
        }
    }
  }
</script>

<style scoped>
  textarea{
    border: 1px solid #ccc;
    border-radius: 5px;
    color: #000;
    font-family: 'Open Sans', sans-serif;
    font-size: 1.2em;
    height: 180px;
    padding: 12px 12px;
    transition: background 0.3s ease-in-out;
    width: 30%;
  }
  textarea:focus {
    outline: none;
    border-color: #9ecaed;
    box-shadow: 0 0 10px #9ecaed;
  }

  .button{
    -webkit-appearance: none;
    background: #009dff;
    border: none;
    border-radius: 6px;
    color: #fff;
    cursor: pointer;
    height: 45px;
    font-family: 'Open Sans', sans-serif;
    font-size: 1.2em;
    letter-spacing: 0.05em;
    text-align: center;
    text-transform: uppercase;
    transition: background 0.3s ease-in-out;
    width: 100px;
  }
  .button:hover {
    background: #00c8ff;
  }
  .button:active {
    background-color: #00c8ff;
    box-shadow: 0 5px #666;
    transform: translateY(3px);
  }

  .select {
    background: #fafdfe;
    height: 45px;
    width: 180px;
    font-size: 1.2em;
    line-height: 30px;
    border: 1px solid #9bc0dd;
    -moz-border-radius: 5px;
    -webkit-border-radius: 5px;
    border-radius: 5px;
  }

  .secondInput {
    margin-top: 30px;
  }
  .submitButton{
    display: inline-block;
    padding-left: 30px;
  }
</style>
