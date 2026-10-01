<template>
  <nav
    :class="[
      'fixed top-0 left-0 right-0 z-50 transition-all duration-300',
      scrolled || isMobileMenuOpen
        ? 'bg-white/90 dark:bg-dark-900/90 backdrop-blur-md shadow-sm border-b border-gray-200 dark:border-dark-700'
        : 'bg-transparent border-b border-transparent'
    ]"
    aria-label="Main navigation"
  >
    <div class="container-max px-4 sm:px-6 lg:px-8">
      <div class="flex items-center justify-between h-16">
        <!-- Logo -->
        <a
          href="#home"
          @click.prevent="go('home')"
          class="flex items-center gap-2 font-bold text-lg"
        >
          <span class="w-9 h-9 rounded-lg bg-gradient-to-br from-primary-600 to-cyan-400 text-white flex items-center justify-center text-sm font-mono">
            AA
          </span>
          <span class="hidden sm:inline text-gray-900 dark:text-white">Abdulqoyum Aliyu</span>
        </a>

        <!-- Desktop Navigation -->
        <div class="hidden md:flex items-center gap-1">
          <a
            v-for="item in navItems"
            :key="item.id"
            :href="`#${item.id}`"
            @click.prevent="go(item.id)"
            :class="[
              'px-3 py-2 rounded-lg text-sm font-medium transition-colors duration-300',
              active === item.id
                ? 'text-primary-600 dark:text-primary-400 bg-primary-50 dark:bg-dark-800'
                : 'text-gray-700 dark:text-gray-300 hover:text-primary-600 dark:hover:text-primary-400'
            ]"
          >
            {{ item.label }}
          </a>
        </div>

        <!-- Theme Toggle & Mobile Menu -->
        <div class="flex items-center gap-2">
          <button
            @click="$emit('toggle-theme')"
            class="p-2 rounded-lg bg-gray-100 dark:bg-dark-800 text-gray-700 dark:text-gray-200 hover:bg-gray-200 dark:hover:bg-dark-700 transition-colors duration-300"
            :aria-label="isDark ? 'Switch to light mode' : 'Switch to dark mode'"
          >
            <Sun v-if="isDark" class="w-5 h-5" />
            <Moon v-else class="w-5 h-5" />
          </button>

          <button
            @click="isMobileMenuOpen = !isMobileMenuOpen"
            class="md:hidden p-2 rounded-lg bg-gray-100 dark:bg-dark-800 text-gray-700 dark:text-gray-200 hover:bg-gray-200 dark:hover:bg-dark-700 transition-colors duration-300"
            :aria-label="isMobileMenuOpen ? 'Close menu' : 'Open menu'"
            :aria-expanded="isMobileMenuOpen"
          >
            <Menu v-if="!isMobileMenuOpen" class="w-5 h-5" />
            <X v-else class="w-5 h-5" />
          </button>
        </div>
      </div>

      <!-- Mobile Navigation -->
      <div v-if="isMobileMenuOpen" class="md:hidden pb-4">
        <div class="flex flex-col gap-1">
          <a
            v-for="item in navItems"
            :key="item.id"
            :href="`#${item.id}`"
            @click.prevent="go(item.id)"
            :class="[
              'px-3 py-2 rounded-lg font-medium transition-colors duration-300',
              active === item.id
                ? 'text-primary-600 dark:text-primary-400 bg-primary-50 dark:bg-dark-800'
                : 'text-gray-700 dark:text-gray-300 hover:bg-gray-100 dark:hover:bg-dark-800'
            ]"
          >
            {{ item.label }}
          </a>
        </div>
      </div>
    </div>
  </nav>
</template>

<script setup>
import { ref, onMounted, onBeforeUnmount } from 'vue'
import { Sun, Moon, Menu, X } from 'lucide-vue-next'

defineProps({
  isDark: Boolean
})

const emit = defineEmits(['toggle-theme', 'navigate'])

const isMobileMenuOpen = ref(false)
const scrolled = ref(false)
const active = ref('home')

const navItems = [
  { id: 'home', label: 'Home' },
  { id: 'about', label: 'About' },
  { id: 'skills', label: 'Skills' },
  { id: 'experience', label: 'Experience' },
  { id: 'projects', label: 'Projects' },
  { id: 'contact', label: 'Contact' }
]

const go = (id) => {
  isMobileMenuOpen.value = false
  emit('navigate', id)
}

const onScroll = () => {
  scrolled.value = window.scrollY > 10
  // Active section = last section whose top has passed the nav bar
  let current = navItems[0].id
  for (const { id } of navItems) {
    const el = document.getElementById(id)
    if (el && el.getBoundingClientRect().top <= 120) current = id
  }
  active.value = current
}

onMounted(() => {
  onScroll()
  window.addEventListener('scroll', onScroll, { passive: true })
})

onBeforeUnmount(() => window.removeEventListener('scroll', onScroll))
</script>
