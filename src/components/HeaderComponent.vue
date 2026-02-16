<template>
  <header class="header">
    <div class="header-content">
      <div class="logo">
        <span class="logo-icon">🎓</span>
        <span class="logo-text">Student Info</span>
      </div>
      <nav>
        <router-link to="/" class="nav-link">
          <span class="nav-icon">🏠</span>
          Home
        </router-link>
        <router-link to="/students" class="nav-link">
          <span class="nav-icon">👥</span>
          Students
        </router-link>
      </nav>
    </div>
  </header>
</template>

<style scoped>
.header {
  position: sticky;
  top: 0;
  z-index: 100;
  background: rgba(15, 23, 42, 0.95);
  backdrop-filter: blur(12px);
  border-bottom: 1px solid rgba(99, 102, 241, 0.2);
  box-shadow: 0 4px 24px rgba(0, 0, 0, 0.3);
}

.header-content {
  max-width: 1200px;
  margin: 0 auto;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 16px 24px;
}

.logo {
  display: flex;
  align-items: center;
  gap: 12px;
}

.logo-icon {
  font-size: 28px;
  filter: drop-shadow(0 0 8px rgba(99, 102, 241, 0.5));
}

.logo-text {
  font-size: 22px;
  font-weight: 700;
  background: linear-gradient(135deg, #6366f1 0%, #8b5cf6 50%, #ec4899 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

nav {
  display: flex;
  gap: 8px;
}

.nav-link {
  display: flex;
  align-items: center;
  gap: 8px;
  padding: 10px 20px;
  text-decoration: none;
  font-weight: 500;
  color: #94a3b8;
  border-radius: 10px;
  transition: all 0.3s ease;
  position: relative;
  overflow: hidden;
}

.nav-link::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: linear-gradient(135deg, rgba(99, 102, 241, 0.1) 0%, rgba(139, 92, 246, 0.1) 100%);
  opacity: 0;
  transition: opacity 0.3s ease;
}

.nav-link:hover {
  color: #ffffff;
  transform: translateY(-2px);
}

.nav-link:hover::before {
  opacity: 1;
}

.nav-link.router-link-active {
  color: #ffffff;
  background: linear-gradient(135deg, #6366f1 0%, #8b5cf6 100%);
  box-shadow: 0 4px 16px rgba(99, 102, 241, 0.4);
}

.nav-icon {
  font-size: 16px;
}

@media (max-width: 640px) {
  .header-content {
    flex-direction: column;
    gap: 16px;
    padding: 16px;
  }
  
  nav {
    width: 100%;
    justify-content: center;
  }
  
  .nav-link {
    padding: 8px 16px;
    font-size: 14px;
  }
}
</style>
