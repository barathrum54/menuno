<template>
  <v-container fill-height>
    <v-responsive class="align-center text-center fill-height">
      <v-img height="200" class="mt-15" src="@/assets/get-started.svg" />

      <div class="pb-14" />

      <v-row justify="center">
        <v-col cols="12" md="8" lg="6">
          <v-card class="register-card">
            <v-card-title class="text-center"
              >These will be used as login details</v-card-title
            >

            <v-card-text>
              <v-form @submit.prevent="registerUser">
                <v-text-field
                  v-model="username"
                  label="Username"
                  required
                  autocomplete="false"
                ></v-text-field>
                <v-text-field
                  v-model="email"
                  label="Email"
                  type="email"
                  required
                  autocomplete="false"
                ></v-text-field>
                <v-text-field
                  v-model="password"
                  label="Password"
                  type="password"
                  required
                  autocomplete="false"
                ></v-text-field>

                <v-btn
                  type="submit"
                  color="primary"
                  class="mt-4"
                  :loading="isLoading"
                  >Register</v-btn
                >
              </v-form>
            </v-card-text>
          </v-card>
        </v-col>
      </v-row>
    </v-responsive>
  </v-container>
</template>

<script setup lang="ts">
import { ref } from "vue";

const username = ref("");
const email = ref("");
const password = ref("");
const isLoading = ref(false);
const registerUser = () => {
  isLoading.value = true;
  setTimeout(() => {
    isLoading.value = false;
  }, 2000);
};
</script>

<style scoped lang="scss">
.register-card {
  max-width: 400px;
  margin: auto;
  padding: 20px;
}
</style>
