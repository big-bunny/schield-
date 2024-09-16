<template>
  <div class="min-h-screen flex flex-col bg-gradient-to-br from-purple-900 to-indigo-800">
    <!-- Main Content Area -->
    <main class="flex-grow">
      <div class="container mx-auto px-6 py-24">
        
        <!-- Video Section -->
        <section class="mb-16">
          <h1 class="text-5xl font-bold text-yellow-300 mb-8 text-center animate-fadeInUp">{{ staffMember.title }}'s Vision</h1>
          <div class="video-container max-w-4xl mx-auto mb-8">
            <video controls class="w-full rounded-lg shadow-lg">
              <source :src="staffMember.video" type="video/mp4">
              Your browser does not support the video tag.
            </video>
          </div>
          <p class="text-2xl text-gray-300 text-center animate-fadeInUp animation-delay-200">
            {{ staffMember.visionStatement }}
          </p>
        </section>
        
        <!-- Gallery Section -->
        <section class="mb-16">
          <h2 class="text-4xl font-bold text-yellow-300 mb-12 text-center animate-fadeInUp animation-delay-400">Gallery</h2>
          <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 gap-8">
            <div v-for="(image, index) in staffMember.gallery" :key="index" class="scroll-animate">
              <img 
                :src="image" 
                :alt="`Gallery Image ${index + 1}`" 
                class="w-full h-64 object-cover rounded-lg shadow-lg"
                @error="(event) => handleImageError(event, index)"
                @load="(event) => handleImageLoad(event, index)"
              >
              <p v-if="imageLoadStatus[index] === 'error'" class="text-red-500 mt-2">
                Error loading image. Path: {{ image }}
              </p>
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
import { ref, onMounted } from 'vue';

const staffMember = ref({
  title: 'Trina Mboya',
  video: '/images/trina.mp4',
  visionStatement: 'Trina Mboya is dedicated to providing quality education and nurturing the next generation of leaders.',
  gallery: [
    '/images/cbc.jpg',
    '/images/jss.jpg',
    '/images/toto.jpg'
  ],
  additionalContent: 'Trina has been a leader in education for over 10 years, constantly innovating and improving the curriculum at Schield Centre.'
});

const imageLoadStatus = ref({});

const handleImageError = (event, index) => {
  console.error(`Failed to load image at index ${index}:`, event.target.src);
  imageLoadStatus.value[index] = 'error';
  // Optionally set a fallback image
  event.target.src = '/path/to/fallback-image.jpg';
};

const handleImageLoad = (event, index) => {
  console.log(`Successfully loaded image at index ${index}:`, event.target.src);
  imageLoadStatus.value[index] = 'success';
};

onMounted(() => {
  const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        entry.target.classList.add('animate-fadeInUp');
      }
    });
  }, { threshold: 0.1 });

  document.querySelectorAll('.scroll-animate').forEach(el => {
    observer.observe(el);
  });
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

.video-container {
  max-width: 100%;
  overflow: hidden;
  border-radius: 0.5rem;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.3);
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