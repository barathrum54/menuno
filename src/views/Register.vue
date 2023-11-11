<template>
  <v-container fill-height>
    <v-responsive class="align-center text-center fill-height">
      <v-img height="200" class="mt-15" src="@/assets/get-started.svg" />

      <div class="pb-14" />

      <v-row justify="center">
        <v-col cols="12" md="8" lg="6">
          <transition name="slide" mode="out-in">
            <component
              :is="registerState"
              @submit-success="registerFormSubmitSuccess"
            ></component>
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
import { Ref } from "vue";
import { shallowRef } from "vue";

type RegisterStateType = typeof RegisterForm | typeof ConfirmAccount;
const registerState: Ref<RegisterStateType | null> = shallowRef(null);

onMounted(() => {
  registerState.value = RegisterForm;
});

const registerFormSubmitSuccess = () => {
  registerState.value = ConfirmAccount;
};
</script>

<style scoped lang="scss">
.slide-enter-active,
.slide-leave-active {
  transition: all ease-out 0.5s;
}

.slide-enter-from {
  transform: translateX(-30%);
}
.slide-leave-to {
  transform: translateX(100%);
  opacity: 0;
}
</style>
