<template>
  <section id="about" class="section-padding bg-white dark:bg-dark-900">
    <div class="container-max">
      <div class="text-center mb-16">
        <h2 class="text-4xl md:text-5xl font-bold text-gray-900 dark:text-white mb-4">
          About <span class="text-gradient">Me</span>
        </h2>
        <p class="text-xl text-gray-600 dark:text-gray-300 max-w-2xl mx-auto">
          Passionate developer with a strong foundation in modern web technologies
        </p>
      </div>
      
      <div class="grid lg:grid-cols-2 gap-12 items-center">
        <!-- Content -->
        <div class="space-y-6">
          <div class="prose prose-lg dark:prose-invert">
            <p class="text-gray-600 dark:text-gray-300 leading-relaxed">
              I'm a dedicated Frontend Developer with expertise in building scalable web applications 
              using modern technologies. With a strong background in both frontend, development, 
              I enjoy creating solutions that make a real impact.
            </p>
            
            <p class="text-gray-600 dark:text-gray-300 leading-relaxed">
              My journey in software development has led me to work with various technologies including 
              React, Vue.js, Node.js, Python, and styling frameworks. I'm passionate about writing clean, 
              efficient code and staying up-to-date with the latest industry trends.
            </p>
          </div>
          
          <!-- Quick Stats -->
          <div class="grid grid-cols-2 gap-6 mt-8">
            <div class="text-center p-6 card">
              <div class="text-3xl font-bold text-primary-600 mb-2">4+</div>
              <div class="text-gray-600 dark:text-gray-300">Years Experience</div>
            </div>
            <div class="text-center p-6 card">
              <div class="text-3xl font-bold text-primary-600 mb-2">10+</div>
              <div class="text-gray-600 dark:text-gray-300">Projects Completed</div>
            </div>
          </div>
          
          <!-- Download CV Button -->
          <div class="pt-6">
            <a 
              href="/Abdulqoyum Aliyu's CV.pdf" 
              download
              class="btn-primary inline-flex items-center gap-2"
            >
              <Download class="w-5 h-5" />
              Download CV
            </a>
          </div>
        </div>
        
        <!-- Image/Visual -->
        <div class="relative">
          <div class="aspect-square rounded-2xl bg-gradient-to-br from-primary-100 to-primary-200 dark:from-primary-900 dark:to-primary-800 p-8 flex items-center justify-center">
            <div class="text-center">
              <Code class="w-24 h-24 text-primary-600 mx-auto mb-4" />
              <h3 class="text-2xl font-bold text-gray-900 dark:text-white mb-2">Clean Code</h3>
              <p class="text-gray-600 dark:text-gray-300">
                Writing maintainable and scalable solutions
              </p>
            </div>
          </div>
          
          <!-- Floating Elements -->
          <div class="absolute -top-4 -right-4 w-20 h-20 bg-primary-500 rounded-full flex items-center justify-center animate-float">
            <Zap class="w-8 h-8 text-white" />
          </div>
          <div class="absolute -bottom-4 -left-4 w-16 h-16 bg-primary-400 rounded-full flex items-center justify-center animate-float" style="animation-delay: 1s;">
            <Rocket class="w-6 h-6 text-white" />
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { Download, Code, Zap, Rocket } from 'lucide-vue-next'
</script>