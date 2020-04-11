// prettier-ignore
<template>
  <div>
    <h1>trans</h1>

    <h3>made with love</h3>
    <TranslateForm v-on:formSubmit="translateText"></TranslateForm>

    <TranslateOutput v-text="translatedText"> </TranslateOutput>
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
          console.log(res);
          this.translatedText = res.body.text[0];
        });
    }
  }
};
</script>
