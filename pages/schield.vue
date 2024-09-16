<template>
      <div class="min-h-screen flex flex-col bg-gradient-to-br from-purple-900 to-indigo-800">
      <!-- Main Content Area -->
      <main class="flex-grow">
        <div class="container mx-auto px-6 py-24">
          
          <!-- Video Section -->
          <section class="mb-16">
            <h1 class="text-5xl font-bold text-yellow-300 mb-8 text-center animate-fadeInUp">{{ staffMember.title }}'s Vision</h1>
            
            <p class="text-2xl text-gray-300 text-center animate-fadeInUp animation-delay-200">
              {{ staffMember.visionStatement }}
            </p>
          </section>
  
          <!-- Gallery Section -->
          <section class="mb-16">
            <h2 class="text-4xl font-bold text-yellow-300 mb-12 text-center animate-fadeInUp animation-delay-400">Gallery</h2>
            <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 gap-8">
              <div v-for="(image, index) in staffMember.gallery" :key="index" class="scroll-animate">
                <img :src="image" alt="Gallery Image" class="w-full h-64 object-cover rounded-lg shadow-lg">
              </div>
            </div>
          </section>
  
          <!-- Additional Content -->
          <section>
            <h2 class="text-4xl font-bold text-yellow-300 mb-12 text-center animate-fadeInUp animation-delay-600">More About {{ staffMember.title }}</h2>
            <p class="text-xl text-gray-300 text-center max-w-4xl mx-auto animate-fadeInUp animation-delay-800">
              {{ staffMember.additionalContent }}
            </p>
          </section>
          
        </div>
      </main>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  
  const staffMember = ref({
    title: 'Patricia Schield', // Replace with dynamic data if needed
    
    visionStatement: 'Patricia Schield is dedicated to providing quality education and nurturing the next generation of leaders.', // Replace with dynamic content
    gallery: [
      '/images/gallery1.jpg', // Replace with dynamic images
      '/images/gallery2.jpg',
      '/images/gallery3.jpg'
    ],
    additionalContent: 'Patricia has been a leader in education for over 20 years, constantly innovating and improving the curriculum at Schield Centre.' // Replace with dynamic content
  });
  </script>
  
  <style scoped>
  @keyframes fadeIn {
    from { opacity: 0; }
    to { opacity: 1; }
  }
  
  @keyframes fadeInUp {
    from {
      opacity: 0;
      transform: translateY(40px);
    }
    to {
      opacity: 1;
      transform: translateY(0);
    }
  }
  
  .animate-fadeIn {
    animation: fadeIn 1s ease-out;
  }
  
  .animate-fadeInUp {
    animation: fadeInUp 0.8s ease-out;
  }
  
  .animation-delay-200 { animation-delay: 0.2s; }
  .animation-delay-400 { animation-delay: 0.4s; }
  .animation-delay-600 { animation-delay: 0.6s; }
  .animation-delay-800 { animation-delay: 0.8s; }
  
  .scroll-animate {
    opacity: 0;
    transform: translateY(40px);
    transition: opacity 0.8s ease-out, transform 0.8s ease-out;
  }
  
  .scroll-animate.animate-fadeInUp {
    opacity: 1;
    transform: translateY(0);
  }
  
 
  .container {
    max-width: 1200px;
  }
  
  h1, h2, h3 {
    letter-spacing: -0.5px;
  }
  
  p {
    line-height: 1.8;
  }
  </style>
  