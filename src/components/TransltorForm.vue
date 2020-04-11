<template>
  <div>
    <form @submit.prevent="formSubmit">
      <input type="text" v-model="textToTranslate" placeholder="Translate" />

      <input type="submit" value="Translate" />

      <select v-model="language">
        <option value="ru">Russian</option>
        <option value="es">Spanish</option>
        <option value="ch">Chinese</option>
        <option value="fr">French</option>
      </select>
    </form>
  </div>
</template>

<script>
export default {

    created() {
    this.language = "ru";
  }, 
  data() {
    return {
      textToTranslate: "",
      language: ""
    };
  },



  methods: {
    formSubmit(e) {
      e.preventDefault();

      this.$emit("formSubmit", this.textToTranslate, this.language);
    }
  }
};
</script>
