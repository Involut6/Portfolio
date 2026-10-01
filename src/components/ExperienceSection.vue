<template>
  <section id="experience" class="section-padding bg-white dark:bg-dark-900">
    <div class="container-max">
      <div class="text-center mb-16">
        <h2 class="text-4xl md:text-5xl font-bold text-gray-900 dark:text-white mb-4">
          Work <span class="text-gradient">Experience</span>
        </h2>
        <p class="text-xl text-gray-600 dark:text-gray-300 max-w-2xl mx-auto">
          My professional journey and key achievements
        </p>
      </div>
      
      <div class="max-w-4xl mx-auto">
        <div class="relative">
          <!-- Timeline Line -->
          <div class="absolute left-8 top-0 bottom-0 w-0.5 bg-primary-200 dark:bg-primary-800"></div>
          
          <!-- Experience Items -->
          <div class="space-y-12">
            <div 
              v-for="(experience, index) in experiences" 
              :key="index"
              class="relative flex items-start"
            >
              <!-- Timeline Dot -->
              <div class="absolute left-6 w-4 h-4 bg-primary-600 rounded-full border-4 border-white dark:border-dark-900 z-10"></div>
              
              <!-- Content -->
              <div class="ml-20 card p-8 w-full">
                <div class="flex flex-col md:flex-row md:items-center md:justify-between mb-4">
                  <div>
                    <h3 class="text-xl font-bold text-gray-900 dark:text-white">{{ experience.role }}</h3>
                    <p class="text-primary-600 font-medium">{{ experience.company }}</p>
                  </div>
                  <div class="flex items-center text-gray-500 dark:text-gray-400 mt-2 md:mt-0">
                    <Calendar class="w-4 h-4 mr-2" />
                    <span class="text-sm">{{ experience.duration }}</span>
                  </div>
                </div>
                
                <p v-if="experience.summary" class="text-gray-600 dark:text-gray-300 mb-4">{{ experience.summary }}</p>

                <!-- Platforms -->
                <div v-if="experience.platforms" class="grid sm:grid-cols-2 gap-4 mb-4">
                  <a
                    v-for="platform in experience.platforms"
                    :key="platform.name"
                    :href="platform.url"
                    target="_blank"
                    rel="noopener noreferrer"
                    class="block p-4 rounded-lg bg-gray-50 dark:bg-dark-800 hover:bg-primary-50 dark:hover:bg-dark-700 transition-colors duration-300"
                  >
                    <div class="flex items-center justify-between mb-1">
                      <span class="font-semibold text-gray-900 dark:text-white">{{ platform.name }}</span>
                      <ExternalLink class="w-4 h-4 text-primary-600" />
                    </div>
                    <p class="text-sm text-gray-600 dark:text-gray-300">{{ platform.description }}</p>
                  </a>
                </div>

                <ul class="list-disc pl-5 space-y-2 text-gray-600 dark:text-gray-300 mb-4">
                  <li v-for="item in experience.responsibilities" :key="item">{{ item }}</li>
                </ul>

                <!-- Technologies -->
                <div class="flex flex-wrap gap-2">
                  <span 
                    v-for="tech in experience.technologies || []" 
                    :key="tech"
                    class="px-3 py-1 bg-primary-100 dark:bg-primary-900 text-primary-700 dark:text-primary-300 rounded-full text-sm"
                  >
                    {{ tech }}
                  </span>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { Calendar, ExternalLink } from 'lucide-vue-next'

const experiences = [
  {
    company: "Finclusion AI",
    role: "Full Stack Engineer",
    location: "Remote",
    duration: "Nov. 2025 – Present",
    summary: "Leading end-to-end development of two core platforms, from architecture through deployment.",
    platforms: [
      {
        name: "CGAS",
        description: "Agriculture and land intelligence system using GIS mapping and spatial analytics.",
        url: "https://dev.cgas.finclusion.ai"
      },
      {
        name: "TeamPulse",
        description: "Project management platform that streamlines operational workflows, with built-in AI features.",
        url: "https://dev.myteampulse.ai"
      }
    ],
    responsibilities: [
      "Delivered 30+ user-facing features across the agriculture intelligence and project management platforms.",
      "Built scalable backend services with NestJS, Prisma ORM, and PostgreSQL, including modular architecture, authentication, and authorization.",
      "Developed interactive GIS mapping interfaces and spatial analytics dashboards for visualizing land and agricultural data in real time.",
      "Designed and optimized PostgreSQL schemas and queries, improving data integrity and query times.",
      "Improved application performance by 30–40% through API optimization, query tuning, lazy loading, and component optimization.",
      "Built AI-powered features for TeamPulse: automated performance validation, AI-driven task creation, and AI-generated presentations from live project data.",
      "Integrated third-party and internal APIs for real-time data sync, reporting, and notifications."
    ],
    technologies: ["NestJS", "Prisma", "PostgreSQL", "Vue.js", "React", "TypeScript", "Tailwind CSS", "GIS", "Claude Code"]
  },
  {
    company: "Securecode Systems",
    role: "Frontend Engineer (Contract)",
    location: "Remote",
    duration: "May 2025 – Jun. 2026",
    responsibilities: [
      "Launched a web-based trade management system that boosted operational efficiency by 70% within 3 months.",
      "Built dashboards that turn complex data into actionable insights.",
      "Integrated role-based access control (RBAC), user management, multi-currency, and location settings."
    ],
    technologies: ["React", "TypeScript", "Tailwind CSS", "Zustand", "Axios"]
  },
  {
    company: "Simplified IQ",
    role: "Frontend Developer",
    location: "Remote",
    duration: "Oct. 2022 – Feb. 2026",
    responsibilities: [
      "Implemented scalable UI solutions, improving performance and reliability by 25%.",
      "Partnered closely with designers to ensure pixel-perfect implementation.",
      "Ran cross-browser testing to guarantee a seamless experience across devices.",
      "Liaised with back-end developers for smooth integration of front-end components."
    ],
    technologies: ["Vue.js", "JavaScript", "Tailwind CSS"]
  },
  {
    company: "Dervac Institute",
    role: "Web Development Tutor",
    location: "Lagos, NGA",
    duration: "Jan. 2023 – Aug. 2023",
    responsibilities: [
      "Built teaching materials with React and Bootstrap that raised student engagement by 30%.",
      "Provided personalized instruction and mentorship on web development concepts.",
      "Facilitated a collaborative learning environment that encouraged knowledge-sharing."
    ],
    technologies: ["React", "Bootstrap"]
  },
  {
    company: "RaydianSoft",
    role: "Frontend Developer",
    location: "Remote",
    duration: "Apr. 2022 – Jan. 2023",
    responsibilities: [
      "Built a responsive website with a team of 3 using Vue 3, increasing user engagement by 30%.",
      "Designed the landing page, authentication flow, and navigation system.",
      "Implemented mobile and tablet layouts for all device sizes."
    ],
    technologies: ["Vue.js", "JavaScript"]
  }
];
</script>
