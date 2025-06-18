<template>
  <footer class="bg-dark-900 text-white py-12">
    <div class="container-max">
      <div class="grid md:grid-cols-3 gap-8 mb-8">
        <!-- Brand -->
        <div>
          <h3 class="text-2xl font-bold text-gradient mb-4">Abdulqoyum Aliyu</h3>
          <p class="text-gray-400 mb-4">
            Frontend Developer passionate about creating innovative web solutions 
            with modern technologies.
          </p>
          <div class="flex space-x-4">
            <a 
              href="https://www.linkedin.com/in/abdulqoyum-aliyu-ba6355183/" 
              target="_blank"
              class="w-10 h-10 bg-dark-800 rounded-lg flex items-center justify-center hover:bg-primary-600 transition-colors duration-300"
            >
              <Linkedin class="w-5 h-5" />
            </a>
            <a 
              href="https://github.com/involut6" 
              target="_blank"
              class="w-10 h-10 bg-dark-800 rounded-lg flex items-center justify-center hover:bg-primary-600 transition-colors duration-300"
            >
              <Github class="w-5 h-5" />
            </a>
            <a 
              href="mailto:olamide2497@gmail.com"
              class="w-10 h-10 bg-dark-800 rounded-lg flex items-center justify-center hover:bg-primary-600 transition-colors duration-300"
            >
              <Mail class="w-5 h-5" />
            </a>
          </div>
        </div>
        
        <!-- Quick Links -->
        <div>
          <h4 class="text-lg font-semibold mb-4">Quick Links</h4>
          <ul class="space-y-2">
            <li>
              <a href="#about" class="text-gray-400 hover:text-white transition-colors duration-300">About</a>
            </li>
            <li>
              <a href="#skills" class="text-gray-400 hover:text-white transition-colors duration-300">Skills</a>
            </li>
            <li>
              <a href="#experience" class="text-gray-400 hover:text-white transition-colors duration-300">Experience</a>
            </li>
            <li>
              <a href="#projects" class="text-gray-400 hover:text-white transition-colors duration-300">Projects</a>
            </li>
            <li>
              <a href="#contact" class="text-gray-400 hover:text-white transition-colors duration-300">Contact</a>
            </li>
          </ul>
        </div>
        
        <!-- Contact Info -->
        <div>
          <h4 class="text-lg font-semibold mb-4">Get In Touch</h4>
          <div class="space-y-2 text-gray-400">
            <p>olamide2497@gmail.com</p>
            <p>Nigeria</p>
            <p>Available for freelance work</p>
          </div>
        </div>
      </div>
      
      <!-- Bottom Bar -->
      <div class="border-t border-dark-700 pt-8 flex flex-col md:flex-row justify-between items-center">
        <p class="text-gray-400 text-sm">
          © {{ currentYear }} Abdulqoyum Aliyu. All rights reserved.
        </p>
        <p class="text-gray-400 text-sm mt-4 md:mt-0">
          Built with Vue.js & Tailwind CSS
        </p>
      </div>
    </div>
  </footer>
</template>

<script setup>
import { computed } from 'vue'
import { Linkedin, Github, Mail } from 'lucide-vue-next'

const currentYear = computed(() => new Date().getFullYear())
</script>