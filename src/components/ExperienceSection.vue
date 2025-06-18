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
                    <h3 class="text-xl font-bold text-gray-900 dark:text-white">{{ experience.title }}</h3>
                    <p class="text-primary-600 font-medium">{{ experience.company }}</p>
                  </div>
                  <div class="flex items-center text-gray-500 dark:text-gray-400 mt-2 md:mt-0">
                    <Calendar class="w-4 h-4 mr-2" />
                    <span class="text-sm">{{ experience.period }}</span>
                  </div>
                </div>
                
                <p class="text-gray-600 dark:text-gray-300 mb-4">{{ experience.description }}</p>
                
                <!-- Technologies -->
                <div class="flex flex-wrap gap-2">
                  <span 
                    v-for="tech in experience.technologies" 
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
import { Calendar } from 'lucide-vue-next'

const experiences = [
  {
    company: "Simplified UX",
    role: "Frontend Developer",
    location: "Remote",
    duration: "Oct. 2022 – Till date",
    responsibilities: [
      "Developed and implemented interactive UI components using Vue.js, Tailwind CSS, and JavaScript frameworks.",
      "Partnered closely with designers to ensure pixel-perfect implementation and user-friendliness.",
      "Conducted thorough cross-browser testing to guarantee a seamless user experience across devices.",
      "Wrote clean, maintainable code adhering to industry best practices and standards.",
      "Liaised with back-end developers for smooth integration of front-end components."
    ]
  },
  {
    company: "RaydianSoft",
    role: "Frontend Developer",
    location: "Remote",
    duration: "Apr. 2022 – Jan. 2023",
    responsibilities: [
      "Collaborated with a team of 3 to build a responsive website using Vue3.",
      "Designed and developed key elements like landing page, authentication flow, and navigation system.",
      "Implemented mobile and tablet layouts for optimal user experience across all devices."
    ]
  },
  {
    company: "Dervac Institute",
    role: "Web Development Tutor",
    location: "Lagos, NGA",
    duration: "Jan. 2023 – Aug. 2023",
    responsibilities: [
      "Cultivated a positive learning environment where students felt comfortable asking questions and seeking help.",
      "Developed innovative teaching materials that improved student engagement.",
      "Provided personalized instruction and mentorship to guide students toward mastery of web development concepts.",
      "Facilitated a collaborative learning environment to encourage knowledge-sharing and problem-solving."
    ]
  }
];

</script>