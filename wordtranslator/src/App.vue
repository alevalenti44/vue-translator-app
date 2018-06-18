<template>
  <div class="text-center" id="app">

    <h1 style="color: #8E8741">Word Translator</h1>
      <br>

    <translateForm v-on:formSubmit="translateText"></translateForm>
    <br/>
    <h1>↓</h1>
    <br>
    <br>
    <translateOutput v-text="translatedText"></translateOutput>
    <br>
    <br>
    <br>
    <p>At the moment, this website only supports English.</p>
  </div>

</template>

<script>
import translateForm from './components/translateForm';
import translateOutput from './components/translateOutput';
import 'bootstrap/dist/css/bootstrap.css';
import 'bootstrap-vue/dist/bootstrap-vue.css';

export default {
  name: 'app',
  components: {
    translateForm,
    translateOutput,
  },
  data: function() {
    return {
      translatedText: '',
    };
  },
  methods: {

    //calls the yandex API and gets the result text + language are emited in translateForm.vue
    translateText: function(text, language) {
      this.$http
        .get(
          'https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20180615T214351Z.4ec50beec8e259db.bf97cada94227f483e4f087b181ccf0a9b451e80&lang=en-' +
            language +
            '&text=' +
            text,
        )
        .then(
          response => {

            //if everything is successful, print the response
            if (response.status == 200) {
              console.log(response);
              this.translatedText = response.body.text['0'];
            }
            //error
            if (response.status == 422) {
              alert('The text cannot be translated');
            }
          },
          response => {

          },
        );
    },
  },
};
</script>

<style>
#app {
}
</style>
