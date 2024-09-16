<template>
  <div class="min-h-screen flex flex-col bg-gradient-to-br from-purple-900 to-indigo-800">
    <!-- Main Content Area -->
    <main class="flex-grow">
      <div class="container mx-auto px-6 py-24">
        <h1 class="text-6xl font-bold text-yellow-300 mb-8 text-center animate-fadeInUp">Meet Our Team</h1>
        <p class="text-2xl mb-16 max-w-4xl mx-auto text-gray-300 text-center animate-fadeInUp animation-delay-200">
          At Schield Centre, our dedicated team is committed to providing exceptional education and support to all students. Meet the leaders who make it all possible.
        </p>

        <!-- Team Section -->
        <h2 class="text-4xl font-bold text-yellow-300 mb-12 text-center animate-fadeInUp animation-delay-400">Our Leadership Team</h2>
        <div class="grid grid-cols-1 lg:grid-cols-2 gap-16 relative">
          <!-- Dividing Line -->
          <div class="absolute top-0 bottom-0 left-1/2 w-px bg-yellow-300 hidden lg:block"></div>

          <div v-for="(staffMember, index) in staff" :key="index" class="scroll-animate relative z-10 flex flex-col lg:flex-row items-center lg:items-start">
            <!-- Link and Icon -->
            <div class="relative lg:w-1/2 flex lg:justify-end lg:pr-6 mb-6 lg:mb-0">
              <NuxtLink :to="staffMember.link" class="group block">
                <div class="rounded-full p-4 border-2 border-yellow-300 hover:bg-yellow-300 transition">
                  <div :class="`program-icon flex items-center justify-center bg-${staffMember.color}-700 rounded-full`">
                    <!-- Use Iconify for icons -->
                    <Icon :icon="staffMember.icon" class="w-8 h-8 text-${staffMember.color}-200" />
                  </div>
                </div>
              </NuxtLink>
            </div>

            <!-- Image and Description -->
            <div class="lg:w-1/2 text-center lg:text-left">
              <div class="program-image-container mb-4">
                <img :src="staffMember.image" :alt="staffMember.title" class="w-full h-48 object-cover rounded-lg">
              </div>
              <h3 :class="`text-2xl font-semibold mb-4 group-hover:text-${staffMember.color}-400`">{{ staffMember.title }}</h3>
              <p class="text-gray-300">{{ staffMember.description }}</p>
            </div>
          </div>
        </div>
      </div>
    </main>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import { Icon } from '@iconify/vue';

// Define staff members with their icons
const staff = ref([
  {
    title: 'Patricia Schield',
    link: '/schield',
    icon: 'heroicons-outline:user', // Update with actual icon name
    color: 'yellow',
    image: '/gallery/pat.jpeg',
    description: 'Founder of Schield Centre and visionary leader, Patricia\'s legacy continues to inspire and guide us.',
  },
  {
    title: 'Mr. Mboya',
    link: '/cbc',
    icon: 'heroicons-outline:book-open', // Update with actual icon name
    color: 'blue',
    image: '/images/bg/ab.jpg',
    description: 'Our Competency-Based Curriculum expert, dedicated to student success and innovation in education.',
  },
  {
    title: 'Mrs Mboya',
    link: '/trina',
    icon: 'heroicons-outline:academic-cap', // Update with actual icon name
    color: 'green',
    image: '/gallery/student3.jpg',
    description: 'Leading our Junior Secondary School program, focusing on academic excellence and personal growth.',
  },
  {
    title: 'Mr. Phelix',
    link: '/special-needs',
    icon: 'heroicons-outline:support', // Update with actual icon name
    color: 'purple',
    image: '/images/programs/schield3.jpg',
    description: 'Champion for special needs education, ensuring every child receives the support they need.',
  }
]);

// IntersectionObserver for scroll animations
onMounted(() => {
  const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        entry.target.classList.add('animate-fadeInUp');
        observer.unobserve(entry.target);
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

.scroll-animate {
  opacity: 0;
  transform: translateY(40px);
  transition: opacity 0.8s ease-out, transform 0.8s ease-out;
}

.scroll-animate.animate-fadeInUp {
  opacity: 1;
  transform: translateY(0);
}

/* Program Card Styles */
.program-icon {
  width: 80px;
  height: 80px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 0 auto 1.5rem;
  transition: all 0.3s ease;
}

.program-image-container {
  overflow: hidden;
  border-radius: 0.5rem;
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
