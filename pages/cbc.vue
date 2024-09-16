<template>
  <div class="min-h-screen bg-gradient-to-br from-purple-700 to-indigo-700 text-white py-16">
    <div class="container mx-auto px-4">
      <h1 class="text-5xl font-bold text-center mb-12 text-yellow-300 font-extrabold">CBC </h1>
      
      <div class="glass-bg rounded-xl p-8 shadow-2xl mb-12">
        <p class="text-lg mb-6">Our Competency-Based Curriculum for grade level provides students with a comprehensive education focused on developing essential skills for the 21st century.</p>
        <h2 class="text-3xl font-semibold mb-6 text-yellow-300 font-bold">Key Features:</h2>
        <ul class="grid grid-cols-1 md:grid-cols-2 gap-4 mb-6">
          <li v-for="feature in features" :key="feature" class="flex items-center text-lg">
            <span class="text-yellow-300 mr-2">
              <i class="fas fa-check-circle"></i>
            </span>
            {{ feature }}
          </li>
        </ul>
      </div>
  
      <div class="grid md:grid-cols-2 gap-12">
        <div class="glass-bg rounded-xl p-8 shadow-lg">
          <h2 class="text-3xl font-semibold mb-6 text-yellow-300 font-bold">Curriculum Subjects</h2>
          <ul class="space-y-2">
            <li v-for="subject in subjects" :key="subject" class="flex items-center text-lg">
              <span class="text-yellow-300 mr-2">
                <i class="fas fa-book"></i>
              </span>
              {{ subject }}
            </li>
          </ul>
        </div>
        <div class="glass-bg rounded-xl p-8 shadow-lg">
          <h2 class="text-3xl font-semibold mb-6 text-yellow-300 font-bold">Our Approach</h2>
          <p class="text-lg mb-4">At Schield Centre, we believe in nurturing well-rounded individuals. Our CBC program goes beyond traditional academics to foster creativity, critical thinking, and practical skills that prepare students for the challenges of the modern world.</p>
          <p class="text-lg">Through project-based learning, collaborative activities, and real-world applications, we ensure that our students not only excel academically but also develop the competencies needed for future success.</p>
        </div>
      </div>

      <!-- New Programs Section -->
      <div class="glass-bg rounded-xl p-8 shadow-lg mt-12">
        <h2 class="text-3xl font-semibold mb-6 text-yellow-300 font-bold">Our Programs</h2>
        <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-6">
          <div v-for="program in programs" :key="program.id" class="rounded-lg shadow-md overflow-hidden">
            <img :src="program.image" :alt="program.title" class="w-full h-40 object-cover">
            <div class="p-4">
              <h3 class="text-xl font-semibold mb-2 text-yellow-400">{{ program.title }}</h3>
              <p class="text-green-200">{{ program.description }}</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
/* Fun and attractive font styling */
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');

h1, h2, p {
  font-family: 'Roboto', sans-serif;
}

h1 {
  font-weight: 700;
}

h2 {
  font-weight: 700;
}

p {
  font-weight: 400;
}

/* Glassy background styling */
.glass-bg {
  background: rgba(255, 255, 255, 0.1); /* Adjust opacity as needed */
  border-radius: 10px;
  backdrop-filter: blur(10px);
  -webkit-backdrop-filter: blur(10px); /* For Safari */
  border: 1px solid rgba(255, 255, 255, 0.2); /* Optional: border for a more defined look */
}
</style>

<script setup>
const features = [
  'Learner-centered approach',
  'Focus on practical skills and competencies',
  'Integration of technology in learning',
  'Regular assessments and feedback',
  'Extracurricular activities for holistic development'
]

const subjects = [
  'Mathematics',
  'English',
  'Kiswahili',
  'Science and Technology',
  'Social Studies',
  'Religious Education',
  'Creative Arts',
  'Physical and Health Education'
]

const programs = [
  {
    id: 1,
    title: 'Art and Design',
    description: 'Support students interested in art and design. Help them explore their creativity and develop their artistic skills.',
    image: '/images/programs/art.jpg',
  },
  {
    id: 2,
    title: 'Chess Club',
    description: 'Empower students with strategic thinking and problem-solving skills through the classic game of chess. Donations help provide equipment and tournament participation opportunities.',
    image: '/images/programs/chess.jpg',
  },
  {
    id: 3,
    title: 'Swimming',
    description: 'Invest in the health and well-being of students. Your support allows us to offer swimming lessons, promote water safety, and build a strong swimming team.',
    image: '/images/programs/swimming.jpg',
  },
  {
    id: 4,
    title: 'Law Club',
    description: 'Spark students\' interest in law and justice. Donations provide resources for mock trials, guest speakers, and educational field trips.',
    image: '/images/programs/law.jpg',
  },
  {
    id: 5,
    title: 'Journalism',
    description: 'Nurture the next generation of storytellers. Your support fuels our school newspaper, yearbook, and media production activities.',
    image: '/images/programs/journalism.jpg',
  },
  {
    id: 6,
    title: 'Cricket Club',
    description: 'Cultivate teamwork, sportsmanship, and a love for cricket. Donations help us maintain equipment, host tournaments, and provide opportunities for students to excel.',
    image: '/images/sliders/slide-2.jpg',
  },
  {
    id: 7,
    title: 'Music',
    description: 'Unleash the musical talents of our students. Your support provides instruments, fosters music appreciation, and encourages participation in concerts and performances.',
    image: '/images/programs/music.jpg',
  },
  {
    id: 8,
    title: 'Debate Team',
    description: 'Equip students with critical thinking, research, and public speaking skills. Donations help us participate in debates, travel to competitions, and develop future leaders.',
    image: '/images/gallery/post-5.jpg',
  },
  {
    id: 9,
    title: 'Coding and Robotics',
    description: 'Fuel the future innovators! Your support provides resources for science labs, technology projects, and field trips to ignite scientific curiosity.',
    image: '/images/programs/c&d.jpg',
  },
]
</script>
