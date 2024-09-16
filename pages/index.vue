<template>
  <div class="min-h-screen flex flex-col bg-gradient-to-br from-purple-900 to-indigo-800">
    <!-- Main Content Area -->
    <main class="flex-grow">
      <div class="container mx-auto px-6 py-24">
        <h1 class="text-6xl font-bold text-yellow-300 mb-8 text-center animate-fadeInUp">Welcome to Schield Centre</h1>
        <p class="text-2xl mb-16 max-w-4xl mx-auto text-gray-300 text-center animate-fadeInUp animation-delay-200">
          Located in the heart of Kajiado, Kenya, Schield Centre is dedicated to providing exceptional education to all children, including those with special needs. Our innovative programs encompass CBC, JSS, Kindergarten (Schield Toto), and specialized curricula for children with unique learning requirements.
        </p>
        
        <!-- About Section -->
        <div class="mb-24 animate-fadeInUp animation-delay-400">
          <h2 class="text-4xl font-bold text-yellow-300 mb-8 text-center">Our Story</h2>
          <div class="bg-purple-800 bg-opacity-50 p-8 rounded-lg shadow-xl">
            <p>
                Schield Centre is a school located in Kajiado, officially established in 2008 by Patricia Schield, an American woman who made a courageous decision. Patricia sold everything she owned and utilized her inheritance to initiate the school. Tragically, Patricia passed away in 2008 before witnessing her dreams come to fruition. Feeling like she had failed, Patricia's dying wish to Joseph Mboya was to establish the school through trustees and fundraising efforts.
              </p>
             
    <p>
      Nestled amidst the picturesque Maasai Plains of Kajiado County stands Schield Centre, a beacon of educational excellence and social empowerment. With a student body of 250 and a faculty of 15 dedicated educators, Schield Centre epitomizes commitment to academic rigor and holistic development.
    </p>

    <p>
      At the helm of this noble endeavor was the visionary Patricia Schield, an indomitable force hailing from Fort Lauderdale, Florida, USA. Fueled by compassion and a fervent desire to uplift disadvantaged children in remote regions, she embarked on a transformative journey. Despite the challenges of age, Patricia embarked on a quest for knowledge, redefining herself as an educator with a singular purpose.
    </p>

    <p>
      Undeterred by adversity, Patricia forged ahead, securing 10 acres of land on the outskirts of Isinya, strategically positioned along the Namanga Highway. Amidst the trials of illness and betrayal, her unwavering resolve persisted, culminating in the establishment of Schield Centre. Entrusting her legacy to the capable hands of Joseph Mboya, a stalwart lawyer, Patricia's vision endured.
    </p>

    <p>
      Although Patricia's earthly journey concluded prematurely, her legacy endured through the stewardship of Joseph Mboya and her devoted family. Trina Donelle Mboya, a luminary in her own right, emerged as a cornerstone in realizing Patricia's dream. Leveraging her global perspective and tenacity, Trina spearheaded fundraising endeavors, propelling essential infrastructure projects forward.
    </p>

    <p>
      Today, Trina Donelle Mboya stands as a revered figure within the Schield Centre community, affectionately known as "Aunty T" to students, parents, and faculty alike. Her multifaceted contributions, ranging from financial stewardship to pedagogical leadership, epitomize the spirit of dedication and service. Guided by a commitment to excellence, she continues to shape the future of Schield Centre with unwavering passion and resolve.
    </p>
  
            <p class="text-gray-300">
              Our journey has been marked by continuous innovation, passionate educators, and a commitment to nurturing every child's potential. Today, we stand proud as a leader in both mainstream and special needs education, shaping the future of Kenya's youth.
            </p>
          </div>
        </div>

        <!-- Programs Section -->
        <h2 class="text-4xl font-bold text-yellow-300 mb-12 text-center animate-fadeInUp animation-delay-600">Our Programs</h2>
        <div class="grid grid-cols-1 lg:grid-cols-2 gap-16 relative">
          <div class="absolute top-0 bottom-0 left-1/2 w-px bg-yellow-300 hidden lg:block"></div>

          <div v-for="(program, index) in programs" :key="program.title" class="scroll-animate relative z-10">
            <NuxtLink :to="program.link" class="program-card group block">
              <div class="program-image-container mb-6">
                <img :src="program.image" :alt="program.title" class="w-full h-48 object-cover rounded-lg">
              </div>
              <div :class="`program-icon bg-${program.color}-700`">
                <Icon :icon="program.icon" class="text-3xl text-${program.color}-200" />
              </div>
              <h3 :class="`text-2xl font-semibold mb-4 group-hover:text-${program.color}-400`">{{ program.title }}</h3>
            </NuxtLink>
            <div class="mt-4">
              <p class="text-gray-300">{{ program.description }}</p>
            </div>
          </div>
        </div>

        <!-- Team Section -->
        <h2 class="text-4xl font-bold text-yellow-300 mb-12 text-center animate-fadeInUp animation-delay-600">Our Team</h2>
        <div class="grid grid-cols-1 lg:grid-cols-2 gap-16 relative">
          <div class="absolute top-0 bottom-0 left-1/2 w-px bg-yellow-300 hidden lg:block"></div>

          <div v-for="(staffMember, index) in staff" :key="staffMember.title" class="scroll-animate relative z-10 flex flex-col lg:flex-row items-center lg:items-start">
            <div class="relative lg:w-1/2 flex lg:justify-end lg:pr-6 mb-6 lg:mb-0">
              <NuxtLink :to="staffMember.link" class="group block">
                <div class="rounded-full p-4 border-2 border-yellow-300 hover:bg-yellow-300 transition">
                  <div :class="`program-icon flex items-center justify-center bg-${staffMember.color}-700 rounded-full`">
                    <Icon :icon="staffMember.icon" class="text-3xl text-${staffMember.color}-200" />
                  </div>
                </div>
              </NuxtLink>
            </div>

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
import { ref, onMounted } from 'vue'
import { Icon } from '@iconify/vue' // Import Icon from Iconify

const programs = ref([
  {
    title: 'CBC',
    link: '/cbc',
    icon: 'heroicons-outline:book-open', // Use Heroicons outline
    color: 'blue',
    image: '/images/bg/rb.jpg',
    description: 'Our Competency-Based Curriculum ensures that all students acquire critical skills and knowledge for the 21st century.'
  },
  {
    title: 'JSS',
    link: '/jss',
    icon: 'heroicons-outline:academic-cap',
    color: 'green',
    image: '/images/bg/study.jpg',
    description: 'The Junior Secondary School program is designed to prepare students for future academic and career success.'
  },
  {
    title: 'Schield Toto',
    link: '/toto',
    icon: 'heroicons-outline:child',
    color: 'yellow',
    image: '/images/students/Teddy.jpeg',
    description: 'Schield Toto provides a nurturing environment for our youngest learners.'
  },
  {
    title: 'Special Needs',
    link: '/special-needs',
    icon: 'heroicons-outline:support',
    color: 'purple',
    image: '/images/bg/3d.jpg',
    description: 'Our specialized programs support children with special needs, ensuring inclusive education.'
  }
])

const staff = ref([
  {
    title: 'Patricia Schield',
    link: '/about',
    icon: 'heroicons-outline:user',
    color: 'yellow',
    image: '/gallery/pat.jpeg',
    description: 'Founder of Schield Centre and passionate advocate for education for all children.'
  },
  {
    title: 'Mr. Mboya',
    link: '/cbc',
    icon: 'heroicons-outline:user-circle',
    color: 'blue',
    image: '/images/bg/ab.jpg',
    description: 'Committed to providing quality education in the Competency-Based Curriculum (CBC).'
  }
])

onMounted(() => {
  const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        entry.target.classList.add('animate-fadeInUp')
        observer.unobserve(entry.target)
      }
    })
  }, { threshold: 0.1 })

  document.querySelectorAll('.scroll-animate').forEach(el => {
    observer.observe(el)
  })
})
</script>

<style scoped>
/* All your existing styles remain the same */
</style>
