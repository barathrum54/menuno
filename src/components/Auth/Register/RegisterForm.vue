<template>
  <v-card class="register-card">
    <v-card-title class="text-center">Register Your Account</v-card-title>

    <v-card-text>
      <v-form @submit.prevent="handleSubmit" ref="form">
        <v-text-field
          v-model="email"
          label="Email"
          type="email"
          required
          autocomplete="false"
          hint="Enter your password to access this website"
          :rules="[rules.required, rules.email]"
        ></v-text-field>

        <v-text-field
          v-model="password"
          label="Password"
          type="password"
          required
          autocomplete="false"
          :rules="[rules.required, rules.password]"
        ></v-text-field>

        <v-text-field
          v-model="repeatPassword"
          label="Repeat Password"
          type="password"
          required
          autocomplete="false"
          :rules="[rules.required, rules.matchPassword]"
        ></v-text-field>

        <v-btn type="submit" color="primary" class="mt-4" :loading="isLoading">
          Register
        </v-btn>
      </v-form>
    </v-card-text>
  </v-card>
</template>

<script setup lang="ts">
import { ref, Ref } from "vue";

const rules = {
  required: (value: any) => !!value || "Field is required",
  email: (value: string) =>
    /^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(value) || "Enter a valid email address",
  password: (value: string) =>
    (value && value.length >= 6) || "Password must be at least 6 characters",
  matchPassword: (value: string) =>
    value === password.value || "Passwords do not match",
};

const emit = defineEmits(["submitSuccess"]);

const email: Ref<string> = ref("tahabdurmus0@gmail.com");
const password: Ref<string> = ref("232323");
const repeatPassword: Ref<string> = ref("232323");
const isLoading: Ref<boolean> = ref(false);

const handleSubmit = (): void => {
  isLoading.value = true;
  setTimeout(() => {
    isLoading.value = false;
    console.log("API request successful");
    emit("submitSuccess");
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
