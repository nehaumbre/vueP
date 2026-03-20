<template>
  <div class="github-profile-viewer">
    <h1 class="app-title">Github Users Search</h1>
    <div class="input-container">
        <input v-model="username" 
               @keyup.enter="getUserProfile" 
               placeholder="Enter GitHub username..." 
               class="username-input" />
    </div>
    <div v-if="userProfie" class="user-profile">
        <img :src="userProfie.avatar_url" alt="User Avatar" class="avatar" />
        <h2 class="user-name">{{ userProfie.name || userProfie.login }}</h2>
        <p class="user-bio">{{ userProfie.bio }}</p>
        <a :href="userProfie.html_url" target="_blank" class="profile-link">View Profile</a>
        <p class="user-bio">Public Repos: {{ userProfie.public_repos }} | Followers: {{ userProfie.followers }}</p>
        <p class="user-bio">Following: {{ userProfie.following }}</p>
        <p class="user-bio">Location: {{ userProfie.location }}</p>
        <p class="user-bio">Email: {{ userProfie.email }}</p>
    </div>
    <div v-else-if="error" class="error-message">{{ error }}</div>
  </div>
</template>

<script setup>
import { ref } from "vue";

const username = ref('');
const userProfie = ref(null);
const error = ref(null);

const getUserProfile = async () => {
  try {
    const response = await fetch(
      `https://api.github.com/users/${username.value}`,
    );
    const data = await response.json();

    if (response.ok) {
      userProfie.value = data;
      error.value = null;
    } else {
      userProfie.value = null;
      error.value = data.message;
    }

    userProfie.value = data;
  } catch (err) {
    console.error("Error fetching user profile:", err);
    error.value = "Failed to fetch user profile. Please try again.";
  }
};
</script>

<style scoped>
.github-profile-viewer {
  max-width: 460px;
  margin: 56px auto;
  padding: 30px 26px;
  border-radius: 28px;
  background:
    radial-gradient(circle at top left, rgba(255, 196, 120, 0.9), transparent 30%),
    radial-gradient(circle at bottom right, rgba(84, 211, 194, 0.28), transparent 34%),
    linear-gradient(145deg, #1a1330 0%, #241742 55%, #2e1c55 100%);
  border: 1px solid rgba(255, 255, 255, 0.1);
  box-shadow: 0 28px 60px rgba(14, 8, 33, 0.45);
  color: #f8f3ff;
  font-family: "Trebuchet MS", "Segoe UI", sans-serif;
  text-align: center;
}

.app-title {
  margin: 0 0 22px;
  font-size: 2rem;
  line-height: 1.1;
  color: #fff7fb;
}

.input-container {
  margin-bottom: 22px;
}

.username-input {
  width: 100%;
  box-sizing: border-box;
  padding: 14px 16px;
  border: 1px solid rgba(255, 255, 255, 0.14);
  border-radius: 16px;
  background: rgba(255, 255, 255, 0.08);
  color: #ffffff;
  font-size: 1rem;
  outline: none;
  transition: border-color 0.18s ease, box-shadow 0.18s ease, transform 0.18s ease;
}

.username-input::placeholder {
  color: #cdbfe3;
}

.username-input:focus {
  border-color: #54d3c2;
  box-shadow: 0 0 0 4px rgba(84, 211, 194, 0.18);
  transform: translateY(-1px);
}

.user-profile {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 10px;
  padding: 22px 18px;
  border-radius: 22px;
  background: rgba(255, 255, 255, 0.08);
  border: 1px solid rgba(255, 255, 255, 0.12);
  backdrop-filter: blur(12px);
  text-align: center;
}

.avatar {
  width: 110px;
  height: 110px;
  border-radius: 50%;
  object-fit: cover;
  border: 4px solid rgba(255, 255, 255, 0.22);
  box-shadow: 0 16px 28px rgba(0, 0, 0, 0.24);
  background: rgba(255, 255, 255, 0.08);
}

.user-name {
  margin: 10px 0 0;
  font-size: 1.45rem;
  font-weight: 800;
  letter-spacing: 0.01em;
  color: #fff4cc;
}

.user-bio {
  max-width: 32ch;
  margin: 0 0 10px;
  padding: 0 6px;
  color: #ddd4f0;
  font-size: 0.98rem;
  line-height: 1.5;
}

.profile-link {
  display: inline-block;
  padding: 11px 18px;
  border-radius: 999px;
  background: linear-gradient(135deg, #ffb347 0%, #ff6f91 100%);
  color: #ffffff;
  text-decoration: none;
  font-weight: 800;
  letter-spacing: 0.02em;
  box-shadow: 0 14px 28px rgba(255, 111, 145, 0.28);
  transition: transform 0.18s ease, filter 0.18s ease;
}

.profile-link:hover {
  transform: translateY(-2px);
  filter: brightness(1.04);
}

.error-message {
  padding: 14px 16px;
  border-radius: 16px;
  background: rgba(255, 109, 132, 0.14);
  border: 1px solid rgba(255, 109, 132, 0.28);
  color: #ffd7df;
  font-weight: 700;
}

@media (max-width: 520px) {
  .github-profile-viewer {
    margin: 24px 14px;
    padding: 24px 18px;
    border-radius: 22px;
  }

  .app-title {
    font-size: 1.7rem;
  }
}
</style>
