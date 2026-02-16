<template>
  <div class="student-card">
    <div class="student-header">
      <h3>{{ name }}</h3>
      <span class="year-badge">{{ year }}</span>
    </div>
    <p class="course">{{ course }}</p>
    <button class="info-btn" @click="toggleDetails">
      <span v-if="showDetails">Hide Details</span>
      <span v-else>Show Details</span>
    </button>
    <transition name="fade">
      <div v-if="showDetails" class="details">
        <span class="details-label">Status:</span> <span class="details-value">Active &amp; Engaged</span><br>
        <span class="details-label">Profile:</span> <span class="details-value">Student in good standing</span>
      </div>
    </transition>
  </div>
</template>

<script setup>
import { ref } from 'vue'

defineProps({
  name: String,
  course: String,
  year: String
})

const showDetails = ref(false)

function toggleDetails() {
  showDetails.value = !showDetails.value
}
</script>

<style scoped>
/* Modern Student Card */
.student-card {
  background: rgba(99, 102, 241, 0.09);
  padding: 26px 20px 18px 20px;
  border-radius: 16px;
  box-shadow: 0 4px 18px rgba(99, 102, 241, 0.10);
  color: #fff;
  transition: box-shadow 0.2s;
  position: relative;
}

.student-card:hover {
  box-shadow: 0 8px 32px rgba(99, 102, 241, 0.18);
}

.student-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 6px;
}

.year-badge {
  background: var(--gradient-primary);
  color: #fff;
  padding: 5px 16px;
  border-radius: 18px;
  font-size: 13px;
  font-weight: 600;
  box-shadow: 0 2px 8px rgba(99, 102, 241, 0.13);
}

.course {
  color: #a5b4fc;
  font-size: 1.05rem;
  margin-bottom: 10px;
}

.info-btn {
  background: var(--gradient-secondary);
  color: #fff;
  border: none;
  padding: 8px 20px;
  border-radius: 8px;
  margin-top: 8px;
  cursor: pointer;
  font-weight: 600;
  font-size: 15px;
  transition: background 0.2s, transform 0.2s;
  box-shadow: 0 2px 8px rgba(20, 184, 166, 0.10);
}

.info-btn:hover {
  background: var(--gradient-primary);
  transform: translateY(-2px) scale(1.03);
}

.details {
  margin-top: 14px;
  background: rgba(20, 184, 166, 0.10);
  border-radius: 8px;
  padding: 10px 14px;
  color: #e0e7ef;
  font-size: 0.98rem;
  text-align: left;
  box-shadow: 0 2px 8px rgba(20, 184, 166, 0.07);
}

.details-label {
  color: #2dd4bf;
  font-weight: 600;
}

.details-value {
  color: #fff;
  font-weight: 500;
}

/* Fade transition for details */
.fade-enter-active, .fade-leave-active {
  transition: opacity 0.3s;
}
.fade-enter-from, .fade-leave-to {
  opacity: 0;
}
</style>
