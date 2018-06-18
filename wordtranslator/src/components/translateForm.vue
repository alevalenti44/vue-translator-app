<template>
  <div id="translateForm">
<form v-on:keyup="formSubmit" class="row justify-content-center" >
  <input type="text" v-model="textToTranslate" placeholder="My name is....." class="col-6 col-md-4 form-control" />
  <select v-model="language" class="btn btn-light dropdown-toggle" style="margin-left: 5px">
    <option value="ru">Russian</option>
    <option value="zh">Chinese</option>
    <option value="tr">Turkish</option>
    <option value="mn">Mongolian</option>
  </select>
</form>
  </div>
</template>


<script>
export default {
  name: 'translateForm',
  data() {
    return {
      textToTranslate: '',
      language: '',
    };
  },

  //The language and text are then used in App.vue to call the Yandex API
  methods: {
    formSubmit(e) {
      this.$emit('formSubmit', this.textToTranslate, this.language);
      e.preventDefault();
    },
  },
};
</script>

<style>
#app {
}
</style>
