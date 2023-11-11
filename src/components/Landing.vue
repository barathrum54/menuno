<template>
  <v-container class="animations-container">
    <v-row>
      <v-col cols="auto" class="animation-col">
        <div class="speech-bubble">
          <v-img class="speech-bubble-img" src="@/assets/speech-bubble.webp" />
          <span>Do you have this?</span>
        </div>
      </v-col>
      <v-col cols="auto" class="animation-col">
        <div class="speech-bubble">
          <v-img class="speech-bubble-img" src="@/assets/speech-bubble.webp" />
          <span>Do you have that one?</span>
        </div>
      </v-col>
    </v-row>
    <v-row class="middle-row">
      <v-col cols="auto" class="animation-col">
        <div class="speech-bubble">
          <v-img class="speech-bubble-img" src="@/assets/speech-bubble.webp" />
          <span>Do you have strawberry jam?</span>
        </div>
      </v-col>
      <v-col cols="auto" class="animation-col">
        <div class="speech-bubble">
          <v-img class="speech-bubble-img" src="@/assets/speech-bubble.webp" />
          <span>You guys have eclair?</span>
        </div>
      </v-col>
    </v-row>
    <v-row class="last-row">
      <v-col cols="auto" class="animation-col">
        <div class="speech-bubble">
          <v-img class="speech-bubble-img" src="@/assets/speech-bubble.webp" />
          <span>Can you call me back when you've got it fresh?</span>
        </div>
      </v-col>
      <v-col cols="auto" class="animation-col">
        <div class="speech-bubble">
          <v-img class="speech-bubble-img" src="@/assets/speech-bubble.webp" />
          <span>How much would it be?</span>
        </div>
      </v-col>
    </v-row>
  </v-container>
  <v-container class="fill-height">
    <v-responsive class="align-center text-center fill-height">
      <v-img height="200" src="@/assets/logo-light.svg" />

      <div class="py-14" />

      <v-row class="d-flex align-center justify-center">
        <v-col cols="auto">
          <v-btn
            color="primary"
            href="/get-started"
            min-width="228"
            rel="noopener noreferrer"
            size="x-large"
            variant="flat"
          >
            <v-icon icon="mdi-arrow-up-bold-box-outline" size="large" start />

            get started for free
          </v-btn>
        </v-col>

        <v-col cols="auto">
          <v-btn
            href="/login"
            min-width="164"
            rel="noopener noreferrer"
            variant="text"
          >
            <v-icon icon="mdi-account-check" size="large" start />

            Log in to your account
          </v-btn>
        </v-col>
      </v-row>
    </v-responsive>
  </v-container>
</template>

<script lang="ts" setup>
import { onUnmounted, ref } from "vue";
import { onMounted } from "vue";

// Function to add and remove the active class
const toggleActiveClass = () => {
  const bubbles = document.querySelectorAll(".speech-bubble");

  // Select a random bubble
  const randomIndex = Math.floor(Math.random() * bubbles.length);
  const randomBubble = bubbles[randomIndex];

  // Add the active class
  if (!randomBubble.classList.contains("active"))
    randomBubble.classList.add("active");

  // Remove the active class after 3 seconds
  setTimeout(() => {
    randomBubble.classList.remove("active");
  }, 3000);
};

// Call the toggleActiveClass function every 2.5 seconds
const intervalId = setInterval(toggleActiveClass, 1000);

onUnmounted(() => {
  // Clear the interval when the component is unmounted
  clearInterval(intervalId);
});

onMounted(() => {
  // Initial call to toggleActiveClass when the component is mounted
  toggleActiveClass();
});
</script>

<style lang="scss" scoped>
.animations-container {
  width: 100%;
  height: 100%;
  left: 0;
  right: 0;
  z-index: 0 !important;
  position: absolute;
  display: flex;
  flex-flow: column;
  .middle-row {
    @media only screen and (max-width: 600px) {
      opacity: 0;
    }
  }
  .last-row {
    @media only screen and (max-width: 600px) {
      margin-top: 20%;
    }
  }
  .animation-col {
    width: 50%;
    display: flex;
    justify-content: flex-start;
    img {
      width: 500px;
    }
    &:nth-of-type(even) {
      justify-content: flex-end;
      .speech-bubble {
        margin-top: -35px;

        .speech-bubble-img {
          transform: scaleX(-1);
        }
      }
    }
    .speech-bubble {
      height: 200px;
      width: 200px;
      display: flex;
      justify-content: center;
      align-items: center;
      position: relative;
      transform: scale(0);
      transition: all 0.5s ease-in-out;
      margin-top: 15px;
      &.active {
        transform: scale(1);
      }
      span {
        color: black;
        position: absolute;
        padding-bottom: 25px;
        font-weight: 900;
        font-size: 1rem;
        width: 70%;
        text-align: center;
        @media only screen and (max-width: 600px) {
          font-size: 0.7rem;
        }
      }
      .speech-bubble-img {
        width: 100%;
        height: 100%;
        object-fit: contain;
        opacity: 0.8;
        position: absolute;
      }
    }
  }
}
</style>
