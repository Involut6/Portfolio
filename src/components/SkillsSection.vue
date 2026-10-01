<template>
  <section id="skills" class="section-padding bg-gray-50 dark:bg-dark-800">
    <div class="container-max">
      <div class="text-center mb-16">
        <h2 class="text-4xl md:text-5xl font-bold text-gray-900 dark:text-white mb-4">
          My <span class="text-gradient">Skills</span>
        </h2>
        <p class="text-xl text-gray-600 dark:text-gray-300 max-w-2xl mx-auto">
          Technologies and tools I work with to bring ideas to life
        </p>
      </div>
      
      <div class="grid md:grid-cols-2 gap-8">
        <!-- Frontend -->
        <div class="card p-8">
          <div class="flex items-center mb-6">
            <div class="w-12 h-12 bg-primary-100 dark:bg-primary-900 rounded-lg flex items-center justify-center mr-4">
              <Monitor class="w-6 h-6 text-primary-600" />
            </div>
            <h3 class="text-xl font-bold text-gray-900 dark:text-white">Frontend</h3>
          </div>
          <div class="space-y-4">
            <SkillBar name="React" level="90" />
            <SkillBar name="Vue.js" level="85" />
            <SkillBar name="JavaScript" level="95" />
            <SkillBar name="TypeScript" level="80" />
            <SkillBar name="HTML/CSS" level="95" />
            <SkillBar name="Tailwind CSS" level="90" />
          </div>
        </div>

        <!-- Backend -->
        <div class="card p-8">
          <div class="flex items-center mb-6">
            <div class="w-12 h-12 bg-primary-100 dark:bg-primary-900 rounded-lg flex items-center justify-center mr-4">
              <Server class="w-6 h-6 text-primary-600" />
            </div>
            <h3 class="text-xl font-bold text-gray-900 dark:text-white">Backend</h3>
          </div>
          <div class="space-y-4">
            <SkillBar name="Node.js" level="85" />
            <SkillBar name="NestJS" level="85" />
            <SkillBar name="REST API Design" level="90" />
            <SkillBar name="PostgreSQL" level="80" />
            <SkillBar name="Prisma ORM" level="85" />
            <SkillBar name="Authentication & Authorization" level="80" />
          </div>
        </div>

        <!-- Cloud & DevOps -->
        <div class="card p-8 md:col-span-2">
          <div class="flex items-center mb-6">
            <div class="w-12 h-12 bg-primary-100 dark:bg-primary-900 rounded-lg flex items-center justify-center mr-4">
              <Cloud class="w-6 h-6 text-primary-600" />
            </div>
            <h3 class="text-xl font-bold text-gray-900 dark:text-white">Cloud & DevOps</h3>
          </div>
          <div class="grid md:grid-cols-2 gap-x-8 gap-y-4">
            <SkillBar name="AWS" level="70" />
            <SkillBar name="Git & Version Control" level="90" />
            <SkillBar name="CI/CD" level="75" />
          </div>
        </div>
      </div>

      <!-- Additional Skills -->
      <div class="mt-16">
        <h3 class="text-2xl font-bold text-center text-gray-900 dark:text-white mb-8">
          Additional Technologies
        </h3>
        <div class="flex flex-wrap justify-center gap-4">
          <span 
            v-for="skill in additionalSkills" 
            :key="skill"
            class="px-4 py-2 bg-white dark:bg-dark-700 rounded-full text-gray-700 dark:text-gray-300 border border-gray-200 dark:border-dark-600 hover:border-primary-300 dark:hover:border-primary-600 transition-colors duration-300"
          >
            {{ skill }}
          </span>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { Monitor, Server, Cloud } from 'lucide-vue-next'
import SkillBar from './SkillBar.vue'

const additionalSkills = [
  'Next.js', 'Redux', 'Zustand', 'Vite', 'Python', 'GIS & Spatial Analytics',
  'AI/LLM Integration', 'Claude Code', 'Bootstrap', 'Sass/SCSS', 'Agile/Scrum'
]
</script>