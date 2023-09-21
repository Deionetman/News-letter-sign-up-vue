<script setup>
import { ref } from "vue";

const emailInput = ref("");
const emailValidation = ref(false);
const listItems = [
  "Product discovery and building what matters",
  "Measuring to ensure updates are a succes",
  "And much more!",
];

const props = defineProps([
  "signUpTitle",
  "signUpText",
  "labelEmail",
  "errorMessage",
  "buttonText",
  "emailInput",
]);

const emit = defineEmits(["submitForm"]);

const submitForm = () => {
  if (emailInput.value.length === 0) {
    alert("Fill in a valid email address");
    emailValidation.value = true;
    return;
  } else {
    emailInput.value = "";
  }

  emit("submitForm");
};
</script>

<template>
  <div class="sign-up">
    <div class="sign-up__left-container">
      <h1 class="sign-up__title">{{ props.signUpTitle }}</h1>
      <p class="sign-up__text">{{ props.signUpText }}</p>
      <ul v-for="(item, idx) in listItems" :key="idx">
        <li>
          <img src="../assets/icon-list.svg" loading="lazy" alt="" />{{ item }}
        </li>
      </ul>
      <form @submit.prevent="submitForm" id="subscribe" class="sign-up__form">
        <div>
          <div class="sign-up__label-container">
            <label for="subscribe" class="sign-up__label">{{
              labelEmail
            }}</label>
            <span class="sign-up__error-message" v-if="emailValidation">{{
              errorMessage
            }}</span>
          </div>
          <input
            :class="{ error: emailValidation }"
            name="subscribe"
            v-model="emailInput"
            type="email"
            placeholder="email@company.com"
          />
          <button class="sign-up__btn">{{ props.buttonText }}</button>
        </div>
      </form>
    </div>
    <div class="sign-up__right-container">
      <img
        src="../assets/illustration-sign-up-desktop.svg"
        class="sign-up__image"
        loading="lazy"
        alt=""
      />
    </div>
  </div>
</template> 

<style lang="scss" scoped>
@import "../../src/assets/styles/_variables.scss";
.sign-up {
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 20px;
  padding: 20px 40px;
  background: white;
  gap: 30px;

  @media #{$media-mobile} {
    flex-direction: column-reverse;
  }

  &__left-container {
    display: flex;
    flex-direction: column;
  }

  &__right-container {
    padding: 20px;

    @media #{$media-mobile} {
      width: 100%;
      padding: 0;
    }

    + img {
      @media #{$media-mobile} {
        width: 100%;
      }
    }
  }

  &__title {
    margin: 10px 0;
  }

  &__text,
  ul {
    font-size: 16px;
    color: hsl(235, 18%, 26%);
    font-weight: 700;
  }

  ul {
    margin: 7px 0;
    padding: 0;
  }

  li {
    display: flex;
    align-items: center;
    font-size: 16px;
    color: hsl(235, 18%, 26%);
    list-style: none;
    margin: 0;

    & > img {
      padding-right: 15px;
    }
  }

  &__form {
    margin: 10px 0;
  }

  &__label {
    display: block;
    font-size: 14px;
    color: hsl(234, 29%, 20%);
    font-weight: 700;
  }

  input {
    display: block;
    width: 100%;
    box-sizing: border-box;
    padding: 10px;
    border: 1px solid hsl(231, 7%, 60%);
    border-radius: 6px;
    margin-top: 5px;

    &::placeholder {
      color: hsl(231, 7%, 60%);
    }
  }

  button {
    display: block;
    width: 100%;
    margin: 20px 0;
    padding: 10px 40px;
    color: white;
    background: hsl(235, 18%, 26%);
    font-size: 14px;
    border: none;

    &:hover {
      color: hsl(235, 18%, 26%);
      background: white;
      border: none;
    }
  }

  &__image {
    width: 100%;
  }
  .error {
    border: 1px solid hsl(4, 100%, 67%);
  }

  &__label-container {
    display: flex;
    align-items: center;
    justify-content: space-between;
    color: hsl(4, 100%, 67%);
    font-weight: 700;
    font-size: 14px;
  }
}
</style>
