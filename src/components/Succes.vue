<script setup>
const props = defineProps(["succesTitle", "buttonText", "succesText"]);
const emit = defineEmits(["dismissForm"]);

const dismissForm = () => {
  emit("dismissForm");
};
</script> 

<template>
  <div class="succes">
    <img src="../assets/icon-success.svg" alt="" />

    <div class="succes__inner">
      <h1 class="succes__title">{{ props.succesTitle }}</h1>
    </div>
    <p class="succes__text">
      {{ succesText }}
    </p>
    <button @click="dismissForm">{{ props.buttonText }}</button>
  </div>
</template>

<style lang="scss" scoped>
@import "../../src/assets/styles/_variables.scss";

.succes {
  display: flex;
  flex-direction: column;
  background: white;
  padding: 40px 50px;
  max-width: 350px;
  border-radius: 30px;

  img {
    width: 50px;
    margin-bottom: 25px;
  }

  &__title {
    margin: 0;
  }

  span {
    font-weight: 700;
  }

  &__text {
    margin: 25px 0;
    font-size: 15px;
  }

  button {
    color: white;
    background: hsl(235, 18%, 26%);
  }
}
</style>