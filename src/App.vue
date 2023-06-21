<template>
  <div>
    <h1>Optional Chaining Demo</h1>
    <button @click="setUser">Set User</button>
    <button @click="breakApp">Break Application</button>
    <button @click="safeRender">Safe Render</button>
    <div v-if="showWithoutChaining">
      User Name Without Optional Chaining: {{ userData.name }}
    </div>
    <div v-if="showWithChaining">
      User Name With Optional Chaining: {{ safeData?.name }}
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';

let userData = ref({ name: 'John Doe' });
let safeData = ref({ name: 'John Doe' });

let showWithoutChaining = ref(false);
let showWithChaining = ref(false);

const setUser = () => {
  userData.value = { name: 'John Doe' };
  safeData.value = { name: 'John Doe' };

  showWithoutChaining.value = true;
  showWithChaining.value = true;
};

const breakApp = () => {
  userData.value = undefined;
  showWithoutChaining.value = true;
  showWithChaining.value = false;
};

const safeRender = () => {
  safeData.value = undefined;
  showWithoutChaining.value = false;
  showWithChaining.value = true;
};
</script>
