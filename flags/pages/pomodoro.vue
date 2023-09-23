<template>
  <div class="w-full h-[100vh] flex flex-col md:flex-row">
    <div
      class="bg-gray-100 md:w-1/3 w-full p-5 flex justify-center items-center flex-col"
    >
      <svg
        height="200px"
        width="200px"
        viewBox="0 0 512 512"
        xmlns="http://www.w3.org/2000/svg"
        fill="#000000"
      >
        <g id="SVGRepo_bgCarrier" stroke-width="0"></g>
        <g
          id="SVGRepo_tracerCarrier"
          stroke-linecap="round"
          stroke-linejoin="round"
        ></g>
        <g id="SVGRepo_iconCarrier">
          <path
            fill="#000000"
            d="M269 24.54c-3.1.11-5.7 0-7.6.21-2.8.25-4.7.45-7.2 2.23l-1 69.32c3 1.18 6.4 2.3 9.7 2.51 4.1.3 6.8-.21 9.2-2.41zm-103.4 37.9c.1 5.95.3 11.01 1.5 14.14 2.3 5.22 7 9.88 26 13.92l22.5 4.78-19.5 11.82c-16.5 10.1-35.2 19.4-51.5 26.5 6.2.7 12.3 1.4 18.2 1.4 17.8-.1 34.6-3.9 55.3-18.1L234 106l.4-24.35c-25.5-5.62-46.5-11.68-68.8-19.21zm181.2 6.49c-19.5 6.69-34.4 10.97-56.4 14.16l.9 18.81-1.7 2.5c-6.8 10-18.4 13.3-27.9 12.7-9.5-.6-17.6-3.9-23.4-7.6l-3.2-2.1-2.2 18c-1.9 17.1-2.1 28.3-5.2 42.4 14.6-10.4 24.4-18.9 36.5-37.3l7.2-10.7 8.1 10c10.9 13 28.8 22.9 48.5 29-5.7-6.5-10.9-14.5-12-25l-1.4-14.1 13.9 4.6c20.6 6.6 26.9 6.1 33.9 3.7 2.9-.9 6.7-2.6 10.6-4.5l-80.7-27.61 27.3-8.15c14.2-4.24 20.9-9.1 24.6-13.94 1-1.5 1.9-3.14 2.6-4.87zM405.5 132l-1.8.4c-17.4 4.2-24.3 9.5-35 13.1-7.4 2.3-15.6 2.8-26.7.9.4.6 1 1.2 1.5 1.8 5 5.5 12.2 11.6 18.8 20.2l13.2 17.2-21.9-2.6c-29.1-3.5-59.4-13.9-80.3-32.9-16.3 21.4-31.5 30.4-57.2 48.6l-25.8 18.4 11.3-29.1c8.4-21.1 9.3-31.3 10.7-46.3-17.3 8.4-33.7 11.5-49.5 11.6-18.7 0-36.5-3.7-55.2-6.4-.4 0-.8.1-1.2.2-59.84 46.2-68.94 115.5-68.87 150.3.17 94.2 26.73 186.7 222.47 190C408.9 490 475.4 388 474.5 293.2c-.8-60.6-12.3-124.4-69-161.2zm-258.4 34.3c13.2-.2 26.4 4.4 28.3 12.4-92.08 41.9-91.59 97.8-105.21 156.8-11.1-56.8-7.31-122.5 55.21-163.6 5.6-3.8 13.8-5.5 21.7-5.6z"
          ></path>
        </g>
      </svg>

      <button class="absolute" @click="toggleValue">
        <svg
          class="mb-[20px]"
          height="100px"
          width="100px"
          viewBox="0 0 72 72"
          id="emoji"
          xmlns="http://www.w3.org/2000/svg"
          fill="#ffffff"
        >
          <g id="SVGRepo_bgCarrier" stroke-width="0"></g>
          <g
            id="SVGRepo_tracerCarrier"
            stroke-linecap="round"
            stroke-linejoin="round"
          ></g>
          <g id="SVGRepo_iconCarrier">
            <g id="color"></g>
            <g id="hair"></g>
            <g id="skin"></g>
            <g id="skin-shadow"></g>
            <g id="line">
              <path
                fill="#ffffff"
                stroke="#ffffff"
                stroke-linejoin="round"
                stroke-miterlimit="10"
                stroke-width="2"
                d="M19.5816,55.6062 c0.4848,0.1782,1.0303,0.297,1.5758,0.297c0.8485,0,1.697-0.297,2.4242-0.7722l30-15.9793l0.303-0.297 c0.7879-0.7722,1.2121-1.7227,1.2121-2.7919c0-1.0692-0.4242-2.0791-1.2121-2.7919l-0.303-0.297l-30-16.0981 c-1.0909-0.8316-2.6667-1.0098-4-0.4752c-1.5152,0.594-2.4848,2.0791-2.4848,3.683v31.8397 C17.0967,53.5272,18.0664,55.0122,19.5816,55.6062z"
              ></path>
            </g>
          </g>
        </svg>
      </button>
      <p class="text-4xl mt-5">
        {{ String(minutes).padStart(2, "0") }}:{{
          String(seconds).padStart(2, "0")
        }}
      </p>
    </div>
    <div
      class="md:w-2/3 w-full flex flex-col items-center p-2 justify-center"
      v-show="value2"
    >
      <p class="text-3xl text-gray-800 mb-6 font-bold flex flex-start w-1/2">
        New task
      </p>
      <!-- <input
        v-model="name"
        type="text"
        class="mb-4 bg-gray-100 border border-gray-300 text-gray-900 text-sm rounded-sm md:w-1/2 w-full py-2 px-1"
        placeholder="name"
      />
      <input
        v-model="email"
        type="email"
        class="bg-gray-100 border border-gray-300 text-gray-900 text-sm rounded-sm md:w-1/2 w-full py-2 px-1"
        placeholder="email"
      /> -->
      <InputField v-model="name" placeholder="Name" type="text" />
      <InputField v-model="email" type="email" placeholder="Email"/>

      <button
        class="bg-gray-800 py-2 px-6 rounded-full md:w-1/2 w-full text-white"
        @click="startTimer"
      >
        Submit
      </button>
      <button
        class="bg-gray-200 py-2 px-6 rounded-full md:w-1/2 w-full text-white mt-4 text-black"
      >
        cancle
      </button>
    </div>
    <div
      class="md:w-2/3 w-full flex flex-col items-center p-2 justify-center"
      v-show="value1"
    >
      <svg
        height="100px"
        width="100px"
        viewBox="0 0 24 24"
        fill="none"
        xmlns="http://www.w3.org/2000/svg"
      >
        <g id="SVGRepo_bgCarrier" stroke-width="0"></g>
        <g
          id="SVGRepo_tracerCarrier"
          stroke-linecap="round"
          stroke-linejoin="round"
        ></g>
        <g id="SVGRepo_iconCarrier">
          <path
            d="M15.24 2H8.76004C5.00004 2 4.71004 5.38 6.74004 7.22L17.26 16.78C19.29 18.62 19 22 15.24 22H8.76004C5.00004 22 4.71004 18.62 6.74004 16.78L17.26 7.22C19.29 5.38 19 2 15.24 2Z"
            stroke="#e8e8e8"
            stroke-width="1.5"
            stroke-linecap="round"
            stroke-linejoin="round"
          ></path>
        </g>
      </svg>
      <div>
        <p></p>
      </div>
    </div>
  </div>
</template>

<script setup>
import InputField from '/components/InputField.vue'; 

import { ref } from "vue";
const value1 = ref(true);
const value2 = ref(false);
const name = ref("");
const email = ref("");
const isRunning = ref(false);
const minutes = ref(0);
const seconds = ref(75);

// design toggle
const toggleValue = () => {
  value1.value = !value1.value;
  value2.value = !value2.value;
};
// end design toggle

// form validation
const validateForm = () => {
  const emailPattern = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
  if (!name.value.trim() || !email.value.trim()) {
    alert("Please fill in all fields.");
    return false;
  }
  if (!emailPattern.test(email.value)) {
    alert("Please enter a valid email address.");
    return false;
  }
  return true;
};

// end form validation

// timer
const startTimer = () => {
  if (!validateForm()) {
    return;
  }
  isRunning.value = true;
  const totalSeconds = minutes.value * 60 + seconds.value;
  let remainingSeconds = totalSeconds;
  const timer = setInterval(() => {
    if (remainingSeconds > 0) {
      remainingSeconds--;
      minutes.value = Math.floor(remainingSeconds / 60);
      seconds.value = remainingSeconds % 60;
    } else {
      clearInterval(timer);
      isRunning.value = false;
    }
  }, 1000);
};
// end timer
</script>

<style scoped>
body {
  @apply bg-gray-100;
}
</style>
