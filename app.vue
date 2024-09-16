<template>
  <div class="min-h-screen flex flex-col bg-gradient-to-br from-blue-500 to-indigo-100">
    <!-- Sticky Header -->
    <Header class="z-50 sticky top-0 shadow-md bg-green-500" />
    
    <!-- Sticky Navbar -->
   
    <!-- Main Content Area -->
    <main class="flex-grow bg-transparent">
      <NuxtPage />
      <!-- add whatsapp chat  icon  -->
    </main>
    
    <!-- Footer -->
    <Footer class="bg-gradient-to-r from-blue-800 to-indigo-900 text-white" />
  </div>
</template>

<script setup>
import { useHead } from '#app'

useHead({
  titleTemplate: '%s - Schield Centre',
  meta: [
    { name: 'description', content: 'Schield Centre - Providing quality education in Kajiado, Kenya' }
  ]
})
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&display=swap');

body {
  font-family: 'Poppins', sans-serif;
  margin: 0; /* Ensure there's no default margin */
  padding: 0; /* Ensure there's no default padding */
  box-sizing: border-box; /* Include padding and border in element's total width and height */
}

h1, h2, h3, h4, h5, h6 {
  margin: 0; /* Remove default margins for headings */
}

/* Ensure good contrast and readability for text in the footer */
.footer-text {
  color: rgba(255, 255, 255, 0.9);
}

/* Header Background Color */
.bg-green-500 {
  background-color: #48bb78; /* Tailwind's green-500 color */
}

/* Navbar Background Color */
.bg-white {
  background-color: #ffffff; /* Ensure the navbar has a solid background color */
}
</style>
