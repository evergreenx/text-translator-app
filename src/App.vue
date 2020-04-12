<template>
  <div class="container mt-5">
    <h1 class="mt-5 mb-5 text-center">TRANSLATOR</h1>

    <TranslateForm v-on:formSubmit="translateText"></TranslateForm>

    <TranslateOutput v-text="translatedText" class="display-3 text-center">
    </TranslateOutput>
  </div>
</template>

<script>
import TranslateForm from "../src/components/TransltorForm";
import TranslateOutput from "../src/components/Translateoutput";

export default {
  data() {
    return {
      translatedText: ""
    };
  },
  components: {
    TranslateForm,
    TranslateOutput
  },

  methods: {
    translateText(text, language) {
      this.$http
        .get(
          "https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20200320T195012Z.dae8cd7773d67eaf.2a3d2702c626500bfca8586d659c54ce42d620cb&lang=" +
            language +
            "&text=" +
            text
        )
        .then(res => {
          this.translatedText = res.body.text[0];
        });
    }
  }
};
</script>

<style>
@import "../src/assets/css/bootstrap.css";

body {
  background-color: rgb(255, 255, 255);
  /* background-image: url( '../src/assets/bg.jpg'); */
  /* background-repeat: no-repeat; */
}

h1{
  font-weight:bolder;
}
</style>
