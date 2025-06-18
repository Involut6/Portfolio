<template>
  <section id="home" class="min-h-screen flex items-center justify-center bg-gradient-to-br from-primary-50 to-white dark:from-dark-900 dark:to-dark-800 relative overflow-hidden">
    <!-- Background Animation -->
    <div class="absolute inset-0 overflow-hidden">
      <div class="absolute -top-40 -right-40 w-80 h-80 bg-primary-200 dark:bg-primary-900 rounded-full mix-blend-multiply filter blur-xl opacity-70 animate-float"></div>
      <div class="absolute -bottom-40 -left-40 w-80 h-80 bg-primary-300 dark:bg-primary-800 rounded-full mix-blend-multiply filter blur-xl opacity-70 animate-float" style="animation-delay: 2s;"></div>
    </div>
    
    <div class="container-max relative z-10">
      <div class="text-center animate-fade-in">
        <!-- Profile Image -->
        <div class="mb-8">
          <div class="w-32 h-32 mx-auto rounded-full bg-gradient-to-r from-primary-400 to-primary-600 p-1 animate-float">
            <div class="w-full h-full rounded-full bg-gray-200 dark:bg-dark-700 flex items-center justify-center">
              <User class="w-16 h-16 text-gray-600 dark:text-gray-400" />
            </div>
          </div>
        </div>
        
        <!-- Main Content -->
        <h1 class="text-5xl md:text-7xl font-bold mb-6 p-4 animate-slide-up">
          <span class="text-gray-900 dark:text-white">Hi, I'm</span>
          <span class="text-gradient block">Abdulqoyum Aliyu</span>
        </h1>
        
        <p class="text-xl md:text-2xl text-gray-600 dark:text-gray-300 mb-4 animate-slide-up" style="animation-delay: 0.2s;">
          Frontend Developer & Software Engineer
        </p>
        
        <p class="text-lg text-gray-500 dark:text-gray-400 mb-8 max-w-2xl mx-auto animate-slide-up" style="animation-delay: 0.4s;">
          Passionate about creating innovative web solutions with modern technologies. 
          Specialized in React, Vue.js, Node.js, and cloud technologies.
        </p>
        
        <!-- CTA Buttons -->
        <div class="flex flex-col sm:flex-row gap-4 justify-center px-4 animate-slide-up" style="animation-delay: 0.6s;">
          <button 
            @click="scrollToSection('projects')"
            class="btn-primary inline-flex items-center gap-2"
          >
            <Briefcase class="w-5 h-5" />
            View My Work
          </button>
          <button 
            @click="scrollToSection('contact')"
            class="btn-secondary inline-flex items-center gap-2"
          >
            <Mail class="w-5 h-5" />
            Get In Touch
          </button>
        </div>
        
        <!-- Social Links -->
        <div class="flex justify-center space-x-6 mt-12 animate-slide-up" style="animation-delay: 0.8s;">
          <a 
            href="https://www.linkedin.com/in/abdulqoyum-aliyu-ba6355183/" 
            target="_blank"
            class="p-3 rounded-full bg-white dark:bg-dark-800 shadow-lg hover:shadow-xl transition-all duration-300 transform hover:scale-110"
          >
            <Linkedin class="w-6 h-6 text-primary-600" />
          </a>
          <a 
            href="https://github.com/involut6" 
            target="_blank"
            class="p-3 rounded-full bg-white dark:bg-dark-800 shadow-lg hover:shadow-xl transition-all duration-300 transform hover:scale-110"
          >
            <Github class="w-6 h-6 text-primary-600" />
          </a>
          <a 
            href="mailto:olamide2497@gmail.com"
            class="p-3 rounded-full bg-white dark:bg-dark-800 shadow-lg hover:shadow-xl transition-all duration-300 transform hover:scale-110"
          >
            <Mail class="w-6 h-6 text-primary-600" />
          </a>
        </div>
      </div>
    </div>
    
    <!-- Scroll Indicator -->
    <div class="absolute bottom-8 left-1/2 transform -translate-x-1/2 animate-bounce">
      <ChevronDown class="w-6 h-6 text-gray-400" />
    </div>
  </section>
</template>

<script setup>
import { User, Briefcase, Mail, Linkedin, Github, ChevronDown } from 'lucide-vue-next'

const scrollToSection = (sectionId) => {
  document.getElementById(sectionId)?.scrollIntoView({ behavior: 'smooth' })
}
</script>