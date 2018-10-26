<template>
  <div class="bottom">
    <!--<input type="text" v-model="outputText" placeholder="这里是翻译后的文本">-->
    <textarea v-model="outputText" placeholder="这里是翻译后的文本"></textarea>
  </div>
</template>

<script>
  export default {
    name: 'TranslateOutput',
    props: ['outputText']
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

  .bottom{
    padding-top: 30px;
  }
</style>


