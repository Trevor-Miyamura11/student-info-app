<template>
  <div class="container">
    <div class="home-hero animate-fade-in">
      <div class="hero-bg"></div>
      <div class="hero-content">
        <div class="hero-badge">Student Portal 2026</div>
        <div class="hero-icon">📚</div>
        <h1>Empowering Students, <span class="gradient-text">One Click</span> at a Time</h1>
        <p class="hero-desc">
          Discover a sleek, modern platform to manage and explore student information.<br>
          Fast, responsive, and beautifully designed for the next generation.
        </p>
        <router-link to="/students" class="cta-btn gradient-btn">
          <span>Explore Directory</span>
          <span class="btn-icon">→</span>
        </router-link>
        <div class="feature-list">
          <div class="feature">
            <span class="feature-emoji">🚀</span>
            <span>Lightning Fast</span>
          </div>
          <div class="feature">
            <span class="feature-emoji">🎨</span>
            <span>Elegant Design</span>
          </div>
          <div class="feature">
            <span class="feature-emoji">🔒</span>
            <span>Secure & Reliable</span>
          </div>
          <div class="feature">
            <span class="feature-emoji">📱</span>
            <span>Mobile Friendly</span>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
/* Modern Home Hero Section */
.home-hero {
  position: relative;
  background: rgba(24, 24, 38, 0.92);
  padding: 64px 40px 56px 40px;
  border-radius: 28px;
  box-shadow: 0 8px 32px rgba(99, 102, 241, 0.18);
  text-align: center;
  max-width: 800px;
  margin: 90px auto 0 auto;
  overflow: hidden;
  border: 1.5px solid rgba(99, 102, 241, 0.18);
}

.hero-bg {
  position: absolute;
  top: -30%;
  left: -30%;
  width: 160%;
  height: 160%;
  background: radial-gradient(circle at 60% 40%, rgba(99, 102, 241, 0.13) 0%, transparent 70%);
  z-index: 0;
  animation: rotate 24s linear infinite;
}

@keyframes rotate {
  from { transform: rotate(0deg); }
  to { transform: rotate(360deg); }
}

.hero-content {
  position: relative;
  z-index: 1;
}

.hero-badge {
  display: inline-block;
  background: var(--gradient-secondary);
  color: #fff;
  font-size: 15px;
  font-weight: 600;
  padding: 6px 22px;
  border-radius: 20px;
  margin-bottom: 18px;
  letter-spacing: 1px;
  box-shadow: 0 2px 10px rgba(20, 184, 166, 0.13);
}

.hero-icon {
  font-size: 70px;
  margin-bottom: 22px;
  filter: drop-shadow(0 0 18px rgba(99, 102, 241, 0.4));
  animation: pulse 2.2s ease-in-out infinite;
}

.hero-content h1 {
  font-size: 2.5rem;
  margin-bottom: 18px;
  font-weight: 700;
  color: #fff;
}

.gradient-text {
  background: var(--gradient-primary);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.hero-desc {
  color: #cbd5e1;
  margin-bottom: 38px;
  line-height: 1.7;
  font-size: 1.1rem;
}

.cta-btn.gradient-btn {
  display: inline-flex;
  align-items: center;
  gap: 10px;
  background: var(--gradient-primary);
  color: #fff;
  padding: 15px 36px;
  border-radius: 14px;
  text-decoration: none;
  font-weight: 600;
  font-size: 17px;
  transition: all 0.3s cubic-bezier(.4,0,.2,1);
  box-shadow: 0 4px 20px rgba(99, 102, 241, 0.22);
  margin-bottom: 30px;
}

.cta-btn.gradient-btn:hover {
  transform: translateY(-3px) scale(1.03);
  box-shadow: 0 8px 32px rgba(99, 102, 241, 0.28);
}

.btn-icon {
  font-size: 20px;
  transition: transform 0.3s cubic-bezier(.4,0,.2,1);
}

.cta-btn.gradient-btn:hover .btn-icon {
  transform: translateX(6px);
}

.feature-list {
  display: flex;
  justify-content: center;
  gap: 36px;
  margin-top: 38px;
  padding-top: 28px;
  border-top: 1px solid rgba(148, 163, 184, 0.18);
  flex-wrap: wrap;
}

.feature {
  display: flex;
  align-items: center;
  gap: 10px;
  color: #a5b4fc;
  font-size: 15px;
  font-weight: 500;
  background: rgba(99, 102, 241, 0.07);
  border-radius: 10px;
  padding: 8px 18px;
  margin-bottom: 8px;
  box-shadow: 0 2px 8px rgba(99, 102, 241, 0.06);
}

.feature-emoji {
  font-size: 20px;
}

@media (max-width: 640px) {
  .home-hero {
    padding: 32px 10px 28px 10px;
    margin: 32px 6px 0 6px;
  }
  .hero-content h1 {
    font-size: 1.5rem;
  }
  .feature-list {
    flex-direction: column;
    gap: 12px;
    padding-top: 18px;
  }
}
</style>
