<template>
  <section id="projects" class="section-padding bg-gray-50 dark:bg-dark-800">
    <div class="container-max">
      <div class="text-center mb-16">
        <h2 class="text-4xl md:text-5xl font-bold text-gray-900 dark:text-white mb-4">
          Featured <span class="text-gradient">Projects</span>
        </h2>
        <p class="text-xl text-gray-600 dark:text-gray-300 max-w-2xl mx-auto">
          Some of my recent work that showcases my skills and creativity
        </p>
      </div>
      
      <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-8">
        <div 
          v-for="(project, index) in projects" 
          :key="index"
          class="card overflow-hidden group"
        >
          <!-- Project Image -->
          <div class="relative h-48 bg-gradient-to-br from-primary-100 to-primary-200 dark:from-primary-900 dark:to-primary-800 overflow-hidden">
            <div class="absolute inset-0 flex items-center justify-center">
              <component :is="project.icon" class="w-16 h-16 text-primary-600" />
            </div>
            <div class="absolute inset-0 bg-black bg-opacity-0 group-hover:bg-opacity-20 transition-all duration-300"></div>
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
                :href="project.liveUrl" 
                target="_blank"
                class="flex items-center text-primary-600 hover:text-primary-700 transition-colors duration-300"
              >
                <ExternalLink class="w-4 h-4 mr-2" />
                Live Demo
              </a>
              <a 
                v-if="project.githubUrl"
                :href="project.githubUrl" 
                target="_blank"
                class="flex items-center text-gray-600 dark:text-gray-400 hover:text-gray-700 dark:hover:text-gray-300 transition-colors duration-300"
              >
                <Github class="w-4 h-4 mr-2" />
                Code
              </a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ExternalLink, Github, Globe, Brain, ShoppingCart, MessageSquare, Plus } from 'lucide-vue-next'

const projects = [
  {
    title: "Dictionary App",
    description: "A comprehensive dictionary application with word definitions, pronunciations, and examples. Features include search functionality and bookmarking.",
    technologies: ["React", "JavaScript", "CSS", "API Integration"],
    liveUrl: "https://my-dictionary-apps.netlify.app/",
    githubUrl: "https://github.com/Involut6/Dictionary-app",
    icon: Globe
  },
  {
    title: "Cheapy Shopping App",
    description: "E-commerce application with product comparison features. Helps users find the best deals across multiple platforms.",
    technologies: ["React", "API Integration", "CSS", "JavaScript"],
    liveUrl: "https://cheapyapp.netlify.app/",
    githubUrl: "https://github.com/Involut6/cheapy",
    icon: ShoppingCart
  },
  {
    title: "DFA TV",
    description: "A streaming platform for movies and shows.",
    technologies: ["Vue.js", "TailwindCSS", "TypeScript"],
    liveUrl: "http://dfatv.com",
    githubUrl: "#",
    icon: MessageSquare
  },
  {
    title: "EnvaAccord",
    description: "A dashboard for managing medical tests and appointment.",
    technologies: ["Vue.js", "TailwindCSS", "TypeScript"],
    liveUrl: "http://envaccord.netlify.app",
    githubUrl: "#",
    icon: Plus
  }
]
</script>