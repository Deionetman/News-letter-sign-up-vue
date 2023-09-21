<script setup>
import Succes from "./components/Succes.vue";
import SignUp from "./components/SignUp.vue";
import { ref } from "vue";

const isSignedUp = ref(false);

const handleSubmit = () => {
  isSignedUp.value = true;
};

const handleDismiss = () => {
  isSignedUp.value = false;
};
</script>

<template>
  <div>
    <div v-if="isSignedUp">
      <Succes
        succesTitle="Thanks for subscribing!"
        succesText="A confirmation email has been sent to your email. Please open it and click
      the button inside to confirm your subscription"
        buttonText="Dismiss message"
        @dismiss-form="handleDismiss"
      />
    </div>
    <div v-else>
      <SignUp
        signUpTitle="Stay updated!"
        signUpText="Join 60.000+ product managers receiving monthly updates on:"
        labelEmail="Email address"
        errorMessage="Valid email required"
        buttonText="Subscribe to monthly newsletter"
        @submit-form="handleSubmit"
      />
    </div>
  </div>
</template>