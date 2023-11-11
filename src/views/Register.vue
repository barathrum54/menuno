<template>
  <v-container fill-height>
    <v-responsive class="align-center text-center fill-height">
      <v-img height="200" class="mt-15" src="@/assets/get-started.svg" />

      <div class="pb-14" />

      <v-row justify="center">
        <v-col cols="12" md="8" lg="6">
          <transition name="slide" mode="out-in">
            <register-form
              @submit-success="registerFormSubmitSuccess"
              v-if="registerState == 'form'"
            ></register-form>
          </transition>
          <transition name="slide" mode="out-in">
            <ConfirmAccount v-if="registerState == 'confirmPending'" />
          </transition>
        </v-col>
      </v-row>
    </v-responsive>
  </v-container>
</template>

<script setup lang="ts">
import RegisterForm from "@/components/Auth/Register/RegisterForm.vue";
import ConfirmAccount from "@/components/Auth/ConfirmAccount.vue";
import { onMounted } from "vue";
import { ref, Ref } from "vue";

const registerState: Ref<string> = ref("form");

onMounted(() => {
  registerState.value = "form";
});

const registerFormSubmitSuccess = () => {
  registerState.value = "confirmPending";
};
</script>

<style scoped lang="scss">
.slide-enter-active,
.slide-leave-active {
  transition: transform 0.5s;
}

.slide-enter,
.slide-leave-to {
  transform: translateX(100%);
}
</style>
