<script setup>
import { ref } from "vue";

// These refs store the current generator settings and the latest password output.
const passwordLength = ref(12);
const includeUppercase = ref("true");
const includeLowercase = ref("true");
const includeNumbers = ref("true");
const includeSpecialCharacters = ref("true");
const generatedPassword = ref("");
const copyMessage = ref("");

// Build a character pool from the selected options, then pick random characters from it.
const generatePassword = () => {
  const lowercaseChars = includeLowercase.value
    ? "abcdefghijklmnopqrstuvwxyz"
    : "";
  const uppercaseChars = includeUppercase.value
    ? "ABCDEFGHIJKLMNOPQRSTUVWXYZ"
    : "";
  const numberChars = includeNumbers.value ? "0123456789" : "";
  const specialChars = includeSpecialCharacters.value ? "!@#$%^&*()-+" : "";

  const allChars = lowercaseChars + uppercaseChars + numberChars + specialChars;

  const password = Array.from(
    { length: passwordLength.value },
    () => allChars[Math.floor(Math.random() * allChars.length)],
  ).join("");
  generatedPassword.value = password;
};

// Copy the generated password to the clipboard when a password is available.
const copyToClipboard = async () => {
  if (!generatedPassword.value) {
    return;
  }

  try {
    await navigator.clipboard.writeText(generatedPassword.value);
    copyMessage.value = "Password copied to clipboard";
    setTimeout(() => {
      copyMessage.value = "";
    }, 2000);
  } catch (error) {
    copyMessage.value = "Copy failed";
    setTimeout(() => {
      copyMessage.value = "";
    }, 2000);
    console.error("Failed to copy password:", error);
  }
};
</script>

<template>
    <div class="password-card">
    <h2>Your Password Generator</h2>

    <div class="result-box">
      <input type="text" readonly :value="generatedPassword" placeholder="Click generate..." />
      <button @click="copyToClipboard" class="copy-btn" v-if="generatedPassword">Copy</button>
    </div>

    <p v-if="copyMessage" class="copy-message" aria-live="polite">{{ copyMessage }}</p>

    <div class="setting">
      <label>Length: {{ passwordLength }}</label>
      <input type="range" v-model.number="passwordLength" min="6" max="32" />
    </div>

    <div class="options">
      <label><input type="checkbox" v-model="includeUppercase" /> ABC</label>
      <label><input type="checkbox" v-model="includeLowercase" /> abc</label>
      <label><input type="checkbox" v-model="includeNumbers" /> 123</label>
      <label><input type="checkbox" v-model="includeSpecialCharacters" /> #$&</label>
    </div>

    <button @click="generatePassword" class="main-btn">Generate</button>
  </div>
</template>

<style scoped>
.password-card {
  --card-bg: rgba(255, 248, 243, 0.88);
  --card-border: rgba(127, 210, 171, 0.24);
  --title-color: #1f5441;
  --text-color: #3d6d5a;
  --muted-color: #73a18e;
  --surface: rgba(255, 255, 255, 0.7);
  --surface-strong: rgba(255, 255, 255, 0.92);
  --accent: #86e3b5;
  --accent-strong: #46b886;
  --accent-soft: #d9f8e8;
  --shadow: 0 24px 60px rgba(70, 184, 134, 0.18);
  max-width: 390px;
  margin: 56px auto;
  padding: 30px 26px;
  border-radius: 28px;
  border: 1px solid var(--card-border);
  background:
    radial-gradient(circle at top left, rgba(203, 255, 228, 0.98), transparent 38%),
    radial-gradient(circle at bottom right, rgba(221, 255, 240, 0.88), transparent 34%),
    linear-gradient(145deg, #fbfffc 0%, #eefdf5 55%, #def9ea 100%);
  box-shadow: var(--shadow);
  backdrop-filter: blur(18px);
  font-family: "Trebuchet MS", "Segoe UI", sans-serif;
  text-align: center;
  color: var(--text-color);
}

.password-card h2 {
  margin: 0 0 22px;
  font-size: 1.7rem;
  font-weight: 800;
  letter-spacing: 0.02em;
  color: var(--title-color);
}

.result-box {
  display: flex;
  align-items: center;
  gap: 10px;
  padding: 12px;
  margin-bottom: 22px;
  border: 1px solid rgba(127, 210, 171, 0.18);
  border-radius: 18px;
  background: var(--surface-strong);
  box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.8);
}

.result-box input {
  width: 100%;
  border: none;
  background: transparent;
  font-family: monospace;
  font-size: 1.1rem;
  outline: none;
  color: var(--title-color);
}

.result-box input::placeholder {
  color: var(--muted-color);
}

.setting,
.options {
  margin-bottom: 18px;
  text-align: left;
}

.setting label,
.options label {
  color: var(--text-color);
  font-weight: 600;
}

.setting input[type="range"] {
  width: 100%;
  margin-top: 10px;
  accent-color: var(--accent-strong);
}

.options {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 12px;
}

.options label {
  display: flex;
  align-items: center;
  gap: 8px;
  padding: 10px 12px;
  border-radius: 14px;
  background: var(--surface);
  border: 1px solid rgba(127, 210, 171, 0.16);
}

.options input[type="checkbox"] {
  accent-color: var(--accent);
}

.main-btn {
  width: 100%;
  padding: 12px;
  background: linear-gradient(135deg, var(--accent) 0%, var(--accent-strong) 100%);
  color: white;
  border: none;
  border-radius: 14px;
  cursor: pointer;
  font-weight: 800;
  letter-spacing: 0.02em;
  box-shadow: 0 16px 28px rgba(70, 184, 134, 0.28);
  transition: transform 0.18s ease, box-shadow 0.18s ease, filter 0.18s ease;
}

.main-btn:hover,
.copy-btn:hover {
  transform: translateY(-1px);
  filter: brightness(1.02);
}

.copy-btn {
  background: linear-gradient(135deg, #f2fff8 0%, var(--accent-soft) 100%);
  color: var(--accent-strong);
  border: none;
  padding: 8px 12px;
  border-radius: 12px;
  font-size: 0.8rem;
  cursor: pointer;
  font-weight: 700;
  white-space: nowrap;
}

.copy-message {
  margin: -8px 0 18px;
  font-size: 0.92rem;
  font-weight: 700;
  color: var(--accent-strong);
}

@media (max-width: 480px) {
  .password-card {
    margin: 24px 14px;
    padding: 24px 18px;
  }

  .options {
    grid-template-columns: 1fr;
  }
}
</style>
