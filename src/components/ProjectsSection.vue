<template>
  <section id="projects" class="section-padding bg-gray-50 dark:bg-dark-800">
    <div class="container-max">
      <div class="text-center mb-12">
        <h2 class="text-4xl md:text-5xl font-bold text-gray-900 dark:text-white mb-4">
          Featured <span class="text-gradient">Projects</span>
        </h2>
        <p class="text-xl text-gray-600 dark:text-gray-300 max-w-2xl mx-auto">
          Some of my recent work that showcases my skills and creativity
        </p>
      </div>

      <!-- Category Filter -->
      <div class="flex flex-wrap justify-center gap-3 mb-12">
        <button
          v-for="category in categories"
          :key="category"
          @click="activeCategory = category"
          :class="[
            'px-4 py-2 rounded-full text-sm font-medium transition-colors duration-300',
            activeCategory === category
              ? 'bg-primary-600 text-white'
              : 'bg-white dark:bg-dark-700 text-gray-700 dark:text-gray-300 hover:bg-primary-100 dark:hover:bg-dark-600'
          ]"
        >
          {{ category }}
        </button>
      </div>

      <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-8">
        <div
          v-for="project in filteredProjects"
          :key="project.title"
          class="card overflow-hidden group"
        >
          <!-- Project Image -->
          <div class="relative h-48 bg-gradient-to-br from-primary-100 to-primary-200 dark:from-primary-900 dark:to-primary-800 overflow-hidden">
            <div class="absolute inset-0 flex items-center justify-center">
              <component :is="project.icon" class="w-16 h-16 text-primary-600" />
            </div>
            <div class="absolute inset-0 bg-black bg-opacity-0 group-hover:bg-opacity-20 transition-all duration-300"></div>
            <span
              v-if="project.featured"
              class="absolute top-3 right-3 px-2 py-1 rounded bg-primary-600 text-white text-xs font-semibold"
            >
              Featured
            </span>
          </div>

          <!-- Project Content -->
          <div class="p-6">
            <h3 class="text-xl font-bold text-gray-900 dark:text-white mb-2">{{ project.title }}</h3>
            <p class="text-gray-600 dark:text-gray-300 mb-4">{{ project.description }}</p>

            <!-- Technologies -->
            <div class="flex flex-wrap gap-2 mb-4">
              <span
                v-for="tech in project.technologies"
                :key="tech"
                class="px-2 py-1 bg-gray-100 dark:bg-dark-700 text-gray-700 dark:text-gray-300 rounded text-sm"
              >
                {{ tech }}
              </span>
            </div>

            <!-- Project Links -->
            <div class="flex space-x-4">
              <a
                v-if="project.liveUrl"
                :href="project.liveUrl"
                target="_blank"
                rel="noopener noreferrer"
                class="flex items-center text-primary-600 hover:text-primary-700 transition-colors duration-300"
              >
                <ExternalLink class="w-4 h-4 mr-2" />
                Live Demo
              </a>
              <a
                v-if="project.githubUrl"
                :href="project.githubUrl"
                target="_blank"
                rel="noopener noreferrer"
                class="flex items-center text-gray-600 dark:text-gray-400 hover:text-gray-700 dark:hover:text-gray-300 transition-colors duration-300"
              >
                <Github class="w-4 h-4 mr-2" />
                Code
              </a>
            </div>
          </div>
        </div>
      </div>

      <div class="text-center mt-12">
        <a
          href="https://github.com/Involut6?tab=repositories"
          target="_blank"
          rel="noopener noreferrer"
          class="btn-secondary inline-flex items-center gap-2"
        >
          <Github class="w-5 h-5" />
          See more on GitHub
        </a>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, computed } from 'vue'
import {
  ExternalLink, Github, Globe, ShoppingCart, Tv, HeartPulse, BookOpen,
  NotebookPen, Bomb, Brain, Dices, Utensils, BarChart3, Newspaper, Layers
} from 'lucide-vue-next'

const projects = [
  {
    title: "DFA TV",
    description: "A streaming platform for movies and shows.",
    technologies: ["Vue.js", "TailwindCSS", "TypeScript"],
    category: "Vue",
    featured: true,
    liveUrl: "http://dfatv.com",
    icon: Tv
  },
  {
    title: "EnvaAccord",
    description: "A dashboard for managing medical tests and appointments.",
    technologies: ["Vue.js", "TailwindCSS", "TypeScript"],
    category: "Vue",
    featured: true,
    liveUrl: "http://envaccord.netlify.app",
    icon: HeartPulse
  },
  {
    title: "Meeqat Blog",
    description: "A blog website built with TypeScript and deployed on Vercel.",
    technologies: ["TypeScript", "Vercel"],
    category: "TypeScript",
    featured: true,
    liveUrl: "https://meeqat-blog.vercel.app",
    githubUrl: "https://github.com/Involut6/Meeqat-blog",
    icon: Newspaper
  },
  {
    title: "SATNMR",
    description: "A website clone built with TypeScript and deployed on Vercel.",
    technologies: ["TypeScript", "Vercel"],
    category: "TypeScript",
    liveUrl: "https://satnmr-copy.vercel.app",
    githubUrl: "https://github.com/Involut6/satnmr-copy",
    icon: Globe
  },
  {
    title: "Dictionary App",
    description: "A dictionary application with word definitions, pronunciations, and examples, powered by a public API.",
    technologies: ["React", "JavaScript", "CSS", "API Integration"],
    category: "React",
    liveUrl: "https://my-dictionary-apps.netlify.app/",
    githubUrl: "https://github.com/Involut6/Dictionary-app",
    icon: BookOpen
  },
  {
    title: "Cheapy Shopping App",
    description: "E-commerce application with product comparison features to help users find the best deals.",
    technologies: ["Vue.js", "API Integration", "CSS", "JavaScript"],
    category: "Vue",
    liveUrl: "https://cheapyapp.netlify.app/",
    githubUrl: "https://github.com/Involut6/cheapy",
    icon: ShoppingCart
  },
  {
    title: "Forcythe",
    description: "A Vue.js web application.",
    technologies: ["Vue.js"],
    category: "Vue",
    githubUrl: "https://github.com/Involut6/Forcythe",
    icon: Layers
  },
  {
    title: "Asalytics",
    description: "An analytics application built with TypeScript.",
    technologies: ["TypeScript"],
    category: "TypeScript",
    githubUrl: "https://github.com/Involut6/Asalytics-app",
    icon: BarChart3
  },
  {
    title: "Food Store",
    description: "An online food store front-end with product browsing.",
    technologies: ["JavaScript", "HTML", "CSS"],
    category: "JavaScript",
    githubUrl: "https://github.com/Involut6/Food-store",
    icon: Utensils
  },
  {
    title: "Note App",
    description: "A simple note-taking app for creating and managing notes.",
    technologies: ["JavaScript", "HTML", "CSS"],
    category: "JavaScript",
    githubUrl: "https://github.com/Involut6/Note-App",
    icon: NotebookPen
  },
  {
    title: "Memory Test",
    description: "A browser memory game that challenges players to match and recall.",
    technologies: ["JavaScript", "HTML", "CSS"],
    category: "JavaScript",
    githubUrl: "https://github.com/Involut6/Memory-Test",
    icon: Brain
  },
  {
    title: "Dice",
    description: "A dice-rolling game built with vanilla JavaScript.",
    technologies: ["JavaScript", "HTML", "CSS"],
    category: "JavaScript",
    githubUrl: "https://github.com/Involut6/Dice",
    icon: Dices
  },
  {
    title: "MineSweeper",
    description: "A classic Minesweeper game.",
    technologies: ["JavaScript"],
    category: "JavaScript",
    githubUrl: "https://github.com/Involut6/MineSweeper",
    icon: Bomb
  }
]

const categories = ['All', ...new Set(projects.map(p => p.category))]
const activeCategory = ref('All')

const filteredProjects = computed(() =>
  activeCategory.value === 'All'
    ? projects
    : projects.filter(p => p.category === activeCategory.value)
)
</script>
