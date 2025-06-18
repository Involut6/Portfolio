<template>
  <nav class="fixed top-0 left-0 right-0 z-50 bg-white/80 dark:bg-dark-900/80 backdrop-blur-md border-b border-gray-200 dark:border-dark-700">
    <div class="container-max">
      <div class="flex items-center justify-between p-4 h-16">
        <!-- Logo -->
        <div class="flex items-center">
          <h1 class="text-xl font-bold text-gradient">Abdulqoyum Aliyu</h1>
        </div>
        
        <!-- Desktop Navigation -->
        <div class="hidden md:flex items-center space-x-8">
          <a 
            v-for="item in navItems" 
            :key="item.id"
            @click="$emit('navigate', item.id)"
            class="text-gray-700 dark:text-gray-300 hover:text-primary-600 dark:hover:text-primary-400 cursor-pointer transition-colors duration-300 font-medium"
          >
            {{ item.label }}
          </a>
        </div>
        
        <!-- Theme Toggle & Mobile Menu -->
        <div class="flex items-center space-x-4">
          <!-- <button 
            @click="$emit('toggle-theme')"
            class="p-2 rounded-lg bg-gray-100 dark:bg-dark-800 hover:bg-gray-200 dark:hover:bg-dark-700 transition-colors duration-300"
          >
            <Sun v-if="isDark" class="w-5 h-5" />
            <Moon v-else class="w-5 h-5" />
          </button> -->
          
          <!-- Mobile Menu Button -->
          <button 
            @click="toggleMobileMenu"
            class="md:hidden p-2 rounded-lg bg-gray-100 dark:bg-dark-800 hover:bg-gray-200 dark:hover:bg-dark-700 transition-colors duration-300"
          >
            <Menu v-if="!isMobileMenuOpen" class="w-5 h-5" />
            <X v-else class="w-5 h-5" />
          </button>
        </div>
      </div>
      
      <!-- Mobile Navigation -->
      <div v-if="isMobileMenuOpen" class="md:hidden p-4 border-t border-gray-200 dark:border-dark-700">
        <div class="flex flex-col space-y-4">
          <a 
            v-for="item in navItems" 
            :key="item.id"
            @click="handleMobileNavClick(item.id)"
            class="text-gray-700 dark:text-gray-300 hover:text-primary-600 dark:hover:text-primary-400 cursor-pointer transition-colors duration-300 font-medium"
          >
            {{ item.label }}
          </a>
        </div>
      </div>
    </div>
  </nav>
</template>

<script setup>
import { ref } from 'vue'
import { Sun, Moon, Menu, X } from 'lucide-vue-next'

defineProps({
  isDark: Boolean
})

defineEmits(['toggle-theme', 'navigate'])

const isMobileMenuOpen = ref(false)

const navItems = [
  { id: 'home', label: 'Home' },
  { id: 'about', label: 'About' },
  { id: 'skills', label: 'Skills' },
  { id: 'experience', label: 'Experience' },
  { id: 'projects', label: 'Projects' },
  { id: 'contact', label: 'Contact' }
]

const toggleMobileMenu = () => {
  isMobileMenuOpen.value = !isMobileMenuOpen.value
}

const handleMobileNavClick = (sectionId) => {
  isMobileMenuOpen.value = false
  setTimeout(() => {
    document.getElementById(sectionId)?.scrollIntoView({ behavior: 'smooth' })
  }, 100)
}
</script>