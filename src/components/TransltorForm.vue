<template>
  <div class="row">
    <div class="col-lg-6 col-md-12 col-sm-12 mb-5 mx-auto">
      <img src="../../src/assets/bg.jpg" class="img-fluid" />
    </div>

    <div class="col-lg-6 col-md-10 col-sm-12 mx-auto">
      <form @submit.prevent="formSubmit">
        <input
          type="text"
          v-model="textToTranslate"
          placeholder="Enter text to Translate eg. hello"
          class="form-control-lg form-control mb-3"
        />
<label>

Choose Language:
</label>
        <select v-model="language" class="form-control-lg form-control mb-3">
          <option value="ru">Russian</option>
          <option value="es">Spanish</option>
          <option value="zh">Chinese</option>
          <option value="fr">French</option>
          <option value="el">Greek</option>
        </select>

        <input
          type="submit"
          value="Translate"
          class="btn btn-block btn-lg btn-secondary mt-5"
        />
      </form>
    </div>
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
<style scoped>
img {
  width: 100%;
}
</style>
