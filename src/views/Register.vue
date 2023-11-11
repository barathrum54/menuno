<template>
  <v-container fill-height>
    <v-responsive class="align-center text-center fill-height">
      <v-img height="200" class="mt-15" src="@/assets/get-started.svg" />

      <div class="pb-14" />

      <v-row justify="center">
        <v-col cols="12" md="8" lg="6">
          <register-form
            @submit-succes="registerFormSubmitSuccess"
          ></register-form>
          <ConfirmAccount/>
        </v-col>
      </v-row>
    </v-responsive>
  </v-container>
</template>

<script setup lang="ts">
import RegisterForm from "@/components/Auth/Register/RegisterForm.vue";
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
