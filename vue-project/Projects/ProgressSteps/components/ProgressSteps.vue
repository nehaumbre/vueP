<template>
  <div class="progress-container">
    <div class="progress-bar">
      <div
        v-for="(step, index) in steps"
        :key="index"
        :class="{ 'step-active': index === currentStep }"
      >
        {{ step }}
      </div>
    </div>
  </div>
  <div class="controls">
    <button :disabled="currentStep === 0" @click="goToPreviousStep" class="btn">
      Previous
    </button>
    <button
      :disabled="currentStep === steps.length - 1"
      @click="goToNextStep"
      class="btn"
    >
      Next
    </button>
  </div>
</template>

<script setup>
import { ref } from "vue";

const steps = ref(["Step1", "Step2", "Step3", "Step4"]);
const currentStep = ref(0);

const goToNextStep = () => {
  if (currentStep.value < steps.value.length - 1) {
    currentStep.value++;
  }
};

const goToPreviousStep = () => {
  if (currentStep.value > 0) {
    currentStep.value--;
  }
};
</script>

<style scoped>
.progress-container {
  max-width: 640px;
  margin: 48px auto 24px;
  padding: 0 16px;
}

.progress-bar {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 12px;
}

.progress-bar > div {
  padding: 12px;
  text-align: center;
  border-radius: 10px;
  background: #f3e8ff;
  color: #5b4278;
  font-weight: 600;
}

.step-active {
  background: #8b5cf6 !important;
  color: #ffffff !important;
}

.controls {
  display: flex;
  justify-content: center;
  gap: 12px;
  margin-top: 12px;
}

.btn {
  padding: 10px 18px;
  border: none;
  border-radius: 8px;
  background: #6d28d9;
  color: #ffffff;
  cursor: pointer;
}

.btn:disabled {
  opacity: 0.5;
  cursor: not-allowed;
}
</style>
