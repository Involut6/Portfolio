<template>
  <div id="app" :class="{ 'dark': isDark }">
    <!-- Navigation -->
    <Navigation 
      :is-dark="isDark" 
      @toggle-theme="toggleTheme"
      @navigate="scrollToSection"
    />
    
    <!-- Hero Section -->
    <HeroSection />
    
    <!-- About Section -->
    <AboutSection />
    
    <!-- Skills Section -->
    <SkillsSection />
    
    <!-- Experience Section -->
    <ExperienceSection />
    
    <!-- Projects Section -->
    <ProjectsSection />
    
    <!-- Contact Section -->
    <ContactSection />
    
    <!-- Footer -->
    <Footer />
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import { useLocalStorage } from '@vueuse/core'
import Navigation from './components/Navigation.vue'
import HeroSection from './components/HeroSection.vue'
import AboutSection from './components/AboutSection.vue'
import SkillsSection from './components/SkillsSection.vue'
import ExperienceSection from './components/ExperienceSection.vue'
import ProjectsSection from './components/ProjectsSection.vue'
import ContactSection from './components/ContactSection.vue'
import Footer from './components/Footer.vue'

const isDark = useLocalStorage('theme-dark', false)

const toggleTheme = () => {
  isDark.value = !isDark.value
}

const scrollToSection = (sectionId) => {
  const element = document.getElementById(sectionId)
  if (element) {
    element.scrollIntoView({ behavior: 'smooth' })
  }
}

onMounted(() => {
  // Apply theme on mount
  if (isDark.value) {
    document.documentElement.classList.add('dark')
  }
})
</script>