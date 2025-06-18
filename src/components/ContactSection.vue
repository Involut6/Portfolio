<template>
  <section id="contact" class="section-padding bg-white dark:bg-dark-900">
    <div class="container-max">
      <div class="text-center mb-16">
        <h2 class="text-4xl md:text-5xl font-bold text-gray-900 dark:text-white mb-4">
          Get In <span class="text-gradient">Touch</span>
        </h2>
        <p class="text-xl text-gray-600 dark:text-gray-300 max-w-2xl mx-auto">
          Let's discuss your next project or opportunity
        </p>
      </div>
      
      <div class="grid lg:grid-cols-2 gap-12 max-w-6xl mx-auto">
        <!-- Contact Info -->
        <div class="space-y-8">
          <div>
            <h3 class="text-2xl font-bold text-gray-900 dark:text-white mb-6">Let's Connect</h3>
            <p class="text-gray-600 dark:text-gray-300 mb-8">
              I'm always interested in hearing about new opportunities and exciting projects. 
              Whether you have a question or just want to say hi, feel free to reach out!
            </p>
          </div>
          
          <!-- Contact Methods -->
          <div class="space-y-6">
            <div class="flex items-center">
              <div class="w-12 h-12 bg-primary-100 dark:bg-primary-900 rounded-lg flex items-center justify-center mr-4">
                <Mail class="w-6 h-6 text-primary-600" />
              </div>
              <div>
                <h4 class="font-medium text-gray-900 dark:text-white">Email</h4>
                <a href="mailto:olamide2497@gmail.com" class="text-primary-600 hover:text-primary-700">
                  olamide2497@gmail.com
                </a>
              </div>
            </div>
            
            <div class="flex items-center">
              <div class="w-12 h-12 bg-primary-100 dark:bg-primary-900 rounded-lg flex items-center justify-center mr-4">
                <Phone class="w-6 h-6 text-primary-600" />
              </div>
              <div>
                <h4 class="font-medium text-gray-900 dark:text-white">Phone</h4>
                <a href="tel:+2348078907474" class="text-primary-600 hover:text-primary-700">
                  +2348078907474
                </a>
              </div>
            </div>
            
            <div class="flex items-center">
              <div class="w-12 h-12 bg-primary-100 dark:bg-primary-900 rounded-lg flex items-center justify-center mr-4">
                <MapPin class="w-6 h-6 text-primary-600" />
              </div>
              <div>
                <h4 class="font-medium text-gray-900 dark:text-white">Location</h4>
                <p class="text-gray-600 dark:text-gray-300">Nigeria</p>
              </div>
            </div>
          </div>
          
          <!-- Social Links -->
          <div class="pt-8">
            <h4 class="font-medium text-gray-900 dark:text-white mb-4">Follow Me</h4>
            <div class="flex space-x-4">
              <a 
                href="https://www.linkedin.com/in/abdulqoyum-aliyu-ba6355183/" 
                target="_blank"
                class="w-12 h-12 bg-primary-100 dark:bg-primary-900 rounded-lg flex items-center justify-center hover:bg-primary-200 dark:hover:bg-primary-800 transition-colors duration-300"
              >
                <Linkedin class="w-6 h-6 text-primary-600" />
              </a>
              <a 
                href="https://github.com/involut6" 
                target="_blank"
                class="w-12 h-12 bg-primary-100 dark:bg-primary-900 rounded-lg flex items-center justify-center hover:bg-primary-200 dark:hover:bg-primary-800 transition-colors duration-300"
              >
                <Github class="w-6 h-6 text-primary-600" />
              </a>
            </div>
          </div>
        </div>
        
        <!-- Contact Form -->
        <div class="card p-8">
          <form @submit.prevent="submitForm" class="space-y-6">
            <div class="grid md:grid-cols-2 gap-6">
              <div>
                <label for="name" class="block text-sm font-medium text-gray-700 dark:text-gray-300 mb-2">
                  Name
                </label>
                <input 
                  type="text" 
                  id="name" 
                  v-model="form.name"
                  required
                  class="w-full px-4 py-3 border border-gray-300 dark:border-dark-600 rounded-lg focus:ring-2 focus:ring-primary-500 focus:border-transparent bg-white dark:bg-dark-700 text-gray-900 dark:text-white"
                  placeholder="Your Name"
                >
              </div>
              <div>
                <label for="email" class="block text-sm font-medium text-gray-700 dark:text-gray-300 mb-2">
                  Email
                </label>
                <input 
                  type="email" 
                  id="email" 
                  v-model="form.email"
                  required
                  class="w-full px-4 py-3 border border-gray-300 dark:border-dark-600 rounded-lg focus:ring-2 focus:ring-primary-500 focus:border-transparent bg-white dark:bg-dark-700 text-gray-900 dark:text-white"
                  placeholder="your@email.com"
                >
              </div>
            </div>
            
            <div>
              <label for="subject" class="block text-sm font-medium text-gray-700 dark:text-gray-300 mb-2">
                Subject
              </label>
              <input 
                type="text" 
                id="subject" 
                v-model="form.subject"
                required
                class="w-full px-4 py-3 border border-gray-300 dark:border-dark-600 rounded-lg focus:ring-2 focus:ring-primary-500 focus:border-transparent bg-white dark:bg-dark-700 text-gray-900 dark:text-white"
                placeholder="Project Discussion"
              >
            </div>
            
            <div>
              <label for="message" class="block text-sm font-medium text-gray-700 dark:text-gray-300 mb-2">
                Message
              </label>
              <textarea 
                id="message" 
                v-model="form.message"
                required
                rows="5"
                class="w-full px-4 py-3 border border-gray-300 dark:border-dark-600 rounded-lg focus:ring-2 focus:ring-primary-500 focus:border-transparent bg-white dark:bg-dark-700 text-gray-900 dark:text-white resize-none"
                placeholder="Tell me about your project..."
              ></textarea>
            </div>
            
            <button 
              type="submit" 
              :disabled="isSubmitting"
              class="w-full btn-primary disabled:opacity-50 disabled:cursor-not-allowed"
            >
              <span v-if="!isSubmitting" class="flex items-center justify-center">
                <Send class="w-5 h-5 mr-2" />
                Send Message
              </span>
              <span v-else class="flex items-center justify-center">
                <div class="w-5 h-5 border-2 border-white border-t-transparent rounded-full animate-spin mr-2"></div>
                Sending...
              </span>
            </button>
          </form>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue'
import { Mail, Phone, MapPin, Linkedin, Github, Send } from 'lucide-vue-next'

const form = ref({
  name: '',
  email: '',
  subject: '',
  message: ''
})

const isSubmitting = ref(false)

const submitForm = async () => {
  isSubmitting.value = true
  
  // Simulate form submission
  await new Promise(resolve => setTimeout(resolve, 2000))
  
  // Reset form
  form.value = {
    name: '',
    email: '',
    subject: '',
    message: ''
  }
  
  isSubmitting.value = false
  
  // Show success message (you can implement a toast notification here)
  alert('Thank you for your message! I\'ll get back to you soon.')
}
</script>