<template>
  <div class="container">
    <!-- STUDENT SHOWCASE -->
    <div class="section-card">
      <h2 class="section-title gradient-title">Meet Our Students</h2>
      <p class="section-desc">A showcase of outstanding students in our program.</p>
      <div class="student-grid">
        <StudentComponent
          v-for="student in students"
          :key="student.id"
          :name="student.name"
          :course="student.course"
          :year="student.year"
        />
      </div>
    </div>

    <!-- COMMUNITY MEMBERS (Redesigned) -->
    <div class="section-card api-section">
      <h2 class="section-title gradient-title">Community Members</h2>
      <p class="section-desc">Meet our vibrant API community, organized and connected worldwide.</p>
      <p v-if="loading" class="loading">Loading community data...</p>
      <p v-if="error" class="error">{{ error }}</p>
      <div v-if="!loading && !error" class="community-grid">
        <div v-for="user in apiUsers" :key="user.id" class="community-card">
          <div class="avatar">
            <img :src="`https://api.dicebear.com/6.x/identicon/svg?seed=${user.username || user.name}`" alt="Avatar" />
          </div>
          <div class="member-info">
            <div class="member-name">{{ user.name }}</div>
            <div class="member-username">@{{ user.username }}</div>
            <div class="member-email">{{ user.email }}</div>
            <div class="member-city">🌍 {{ user.address?.city || 'Unknown City' }}</div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import StudentComponent from '../components/StudentComponent.vue'

const students = ref([
  { id: 1, name: 'Ava Martinez', course: 'BSIT', year: '4th Year' },
  { id: 2, name: 'Liam Johnson', course: 'BSCS', year: '3rd Year' },
  { id: 3, name: 'Sophia Lee', course: 'BSIT', year: '2nd Year' },
  { id: 4, name: 'Noah Smith', course: 'BSCS', year: '1st Year' }
])

const apiUsers = ref([])
const loading = ref(true)
const error = ref(null)

onMounted(async () => {
  try {
    const response = await fetch('https://jsonplaceholder.typicode.com/users')
    if (!response.ok) throw new Error('Failed to fetch API')

    apiUsers.value = await response.json()
  } catch (err) {
    error.value = err.message
  } finally {
    loading.value = false
  }
})
</script>

<style scoped>
/* Section Card Modernized */
.section-card {
  background: rgba(30, 41, 59, 0.93);
  padding: 44px 32px 36px 32px;
  border-radius: 20px;
  box-shadow: 0 8px 32px rgba(99, 102, 241, 0.13);
  margin-bottom: 48px;
  max-width: 900px;
  margin-left: auto;
  margin-right: auto;
}

.section-title {
  margin-bottom: 12px;
  color: #fff;
  font-weight: 700;
  font-size: 2rem;
  letter-spacing: 1px;
}

.gradient-title {
  background: var(--gradient-primary);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.section-desc {
  color: #a5b4fc;
  margin-bottom: 28px;
  font-size: 1.08rem;
  text-align: center;
}

.student-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
  gap: 24px;
}

.api-section {
  margin-top: 24px;
}

/* Community Members Grid */
.community-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
  gap: 30px;
  margin-top: 18px;
}

.community-card {
  display: flex;
  align-items: center;
  background: rgba(99, 102, 241, 0.10);
  border-radius: 14px;
  padding: 18px 16px;
  box-shadow: 0 2px 10px rgba(99, 102, 241, 0.09);
  transition: box-shadow 0.2s, background 0.2s;
  color: #fff;
  gap: 18px;
}

.community-card:hover {
  background: rgba(99, 102, 241, 0.18);
  box-shadow: 0 8px 32px rgba(99, 102, 241, 0.18);
}

.avatar {
  width: 54px;
  height: 54px;
  border-radius: 50%;
  overflow: hidden;
  background: #fff;
  box-shadow: 0 2px 8px rgba(99, 102, 241, 0.13);
  flex-shrink: 0;
}
.avatar img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.member-info {
  display: flex;
  flex-direction: column;
  gap: 2px;
}
.member-name {
  font-size: 1.15rem;
  font-weight: 700;
  color: #a5b4fc;
}
.member-username {
  font-size: 0.98rem;
  color: #38bdf8;
  font-weight: 500;
}
.member-email {
  font-size: 0.95rem;
  color: #f1f5f9;
}
.member-city {
  font-size: 0.92rem;
  color: #14b8a6;
  margin-top: 2px;
}

.loading {
  color: #14b8a6;
  font-weight: 500;
}

.error {
  color: #f87171;
  font-weight: 500;
}

@media (max-width: 700px) {
  .section-card {
    padding: 22px 6px 18px 6px;
  }
  .student-grid {
    gap: 12px;
  }
  .api-grid {
    gap: 8px;
  }
}
</style>
