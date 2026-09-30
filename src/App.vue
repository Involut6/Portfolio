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
import { watchEffect } from 'vue'
import { useLocalStorage } from '@vueuse/core'
import Navigation from './components/Navigation.vue'
import HeroSection from './components/HeroSection.vue'
import AboutSection from './components/AboutSection.vue'
import SkillsSection from './components/SkillsSection.vue'
import ExperienceSection from './components/ExperienceSection.vue'
import ProjectsSection from './components/ProjectsSection.vue'
import ContactSection from './components/ContactSection.vue'
import Footer from './components/Footer.vue'

const prefersDark = window.matchMedia?.('(prefers-color-scheme: dark)').matches ?? false
const isDark = useLocalStorage('theme-dark', prefersDark)

const toggleTheme = () => {
  isDark.value = !isDark.value
}

const scrollToSection = (sectionId) => {
  const element = document.getElementById(sectionId)
  if (element) {
    element.scrollIntoView({ behavior: 'smooth' })
  }
}

watchEffect(() => {
  document.documentElement.classList.toggle('dark', isDark.value)
})
</script>
