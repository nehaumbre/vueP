<template>
  <div class="form-shell">
    <form @submit.prevent="submitForm" class="custom-form">
      <div class="form-header">
        <p class="eyebrow">Starter Form</p>
        <h2>Create Your Account</h2>
        <p class="subtitle">Simple form with built-in validation.</p>
      </div>

      <div class="form-group">
        <label for="name">Name</label>
        <input type="text" id="name" v-model="formData.name" placeholder="Enter your full name">
        <span v-if="!isNameValid" class="error">Name is required</span>
      </div>

      <div class="form-group">
        <label for="email">Email</label>
        <input type="email" id="email" v-model="formData.email" placeholder="Enter your email">
        <span v-if="!isEmailValid" class="error">Please enter a valid email address</span>
      </div>

      <div class="form-group">
        <label for="password">Password</label>
        <input type="password" id="password" v-model="formData.password" placeholder="Minimum 8 characters">
        <span v-if="!isPasswordValid" class="error">Password must be at least 8 characters long</span>
      </div>

      <div class="form-group">
        <label for="confirmPassword">Confirm Password</label>
        <input type="password" id="confirmPassword" v-model="formData.confirmPassword" placeholder="Re-enter password">
        <span v-if="!doPasswordsMatch" class="error">Passwords do not match</span>
      </div>

      <button type="submit" :disabled="!isFormValid" class="submit-button">Submit</button>
    </form>
  </div>
</template>

<script setup>
import { ref, computed } from "vue";

const formData = ref({
  name: "",
  email: "",
  password: "",
  confirmPassword: "",
});

const isNameValid = computed(() => formData.value.name.trim() !== "");
const isEmailValid = computed(() =>
  /^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(formData.value.email),
);
const isPasswordValid = computed(() => formData.value.password.length >= 8);
const doPasswordsMatch = computed(
  () => formData.value.password === formData.value.confirmPassword,
);

const isFormValid = computed(
  () =>
    isNameValid.value &&
    isEmailValid.value &&
    isPasswordValid.value &&
    doPasswordsMatch.value,
);

const submitForm = ()=>{  
    if(isFormValid.value){  
        alert("Form submitted successfully!")
    }else{  
        alert("Please fix the errors in the form before submitting.")
    }
}
</script>

<style scoped>
.form-shell,
.custom-form,
.form-group,
.form-group input,
.submit-button {
  box-sizing: border-box;
}

.form-shell {
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 24px;
  background:
    radial-gradient(circle at top left, rgba(255, 110, 180, 0.28), transparent 28%),
    radial-gradient(circle at bottom right, rgba(255, 160, 210, 0.18), transparent 32%),
    linear-gradient(180deg, #18121f 0%, #22162d 52%, #2b1933 100%);
}

.custom-form {
  width: min(100%, 430px);
  padding: 30px 26px;
  border-radius: 24px;
  background: rgba(34, 24, 45, 0.88);
  border: 1px solid rgba(255, 121, 184, 0.18);
  box-shadow: 0 24px 48px rgba(8, 5, 15, 0.45);
  backdrop-filter: blur(14px);
  font-family: "Trebuchet MS", "Segoe UI", sans-serif;
}

.form-header {
  margin-bottom: 22px;
  text-align: center;
}

.eyebrow {
  margin: 0 0 8px;
  color: #ff9ecd;
  font-size: 0.78rem;
  font-weight: 800;
  letter-spacing: 0.18em;
  text-transform: uppercase;
}

.form-header h2 {
  margin: 0;
  color: #fff3fa;
  font-size: 2rem;
  line-height: 1.12;
}

.subtitle {
  margin: 10px 0 0;
  color: #d8bdd0;
  font-size: 0.97rem;
}

.form-group {
  margin-bottom: 18px;
}

.form-group label {
  display: block;
  margin-bottom: 8px;
  color: #f9d9ea;
  font-size: 0.95rem;
  font-weight: 700;
}

.form-group input {
  width: 100%;
  max-width: 100%;
  padding: 13px 15px;
  border: 1px solid rgba(255, 133, 193, 0.22);
  border-radius: 16px;
  background: rgba(255, 245, 251, 0.08);
  color: #fff3fa;
  font-size: 0.98rem;
  outline: none;
  transition: border-color 0.18s ease, box-shadow 0.18s ease, transform 0.18s ease;
}

.form-group input::placeholder {
  color: #b997ad;
}

.form-group input:focus {
  border-color: #ff7cbc;
  box-shadow: 0 0 0 4px rgba(255, 124, 188, 0.16);
  transform: translateY(-1px);
}

.error {
  display: inline-block;
  margin-top: 8px;
  color: #ff8fa8;
  font-size: 0.87rem;
  font-weight: 700;
}

.submit-button {
  width: 100%;
  margin-top: 8px;
  padding: 14px 18px;
  border: none;
  border-radius: 16px;
  background: linear-gradient(135deg, #ff7cbc 0%, #ff5ca8 52%, #db3d8a 100%);
  color: #fff7fb;
  font-size: 1rem;
  font-weight: 800;
  letter-spacing: 0.02em;
  cursor: pointer;
  box-shadow: 0 14px 28px rgba(219, 61, 138, 0.35);
  transition: transform 0.18s ease, filter 0.18s ease, box-shadow 0.18s ease;
}

.submit-button:hover:not(:disabled) {
  transform: translateY(-2px);
  filter: brightness(1.03);
}

.submit-button:disabled {
  cursor: not-allowed;
  background: linear-gradient(135deg, #8f6b80 0%, #6f5769 100%);
  box-shadow: none;
  color: #f0dde8;
}

@media (max-width: 520px) {
  .form-shell {
    padding: 14px;
  }

  .custom-form {
    padding: 22px 18px;
    border-radius: 20px;
  }

  .form-header h2 {
    font-size: 1.65rem;
  }
}
</style>
