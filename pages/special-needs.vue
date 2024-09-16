<template>
  <div class="min-h-screen bg-gradient-to-br from-purple-900 to-indigo-900 text-white py-16">
    <div class="container mx-auto px-4">
      <h1 class="text-5xl font-bold text-center mb-12 text-yellow-300 font-extrabold">Special Needs Education</h1>
      
      <p class="text-xl text-center mb-12 max-w-3xl mx-auto font-semibold">Schield Centre is committed to providing an inclusive environment where children with special needs can thrive. We offer specialized programs tailored to the unique needs of each student.</p>
      
      <div class="grid grid-cols-1 md:grid-cols-2 gap-12 mb-16">
        <div class="glass-bg p-8 rounded-xl shadow-lg transform hover:scale-105 transition-all duration-300">
          <h3 class="text-2xl font-semibold text-yellow-300 mb-4">Individualized Education Plans</h3>
          <p class="text-lg">Each student receives a personalized education plan that addresses their specific learning needs and goals, ensuring they receive the support they need to succeed.</p>
        </div>
        <div class="glass-bg p-8 rounded-xl shadow-lg transform hover:scale-105 transition-all duration-300">
          <h3 class="text-2xl font-semibold text-yellow-300 mb-4">Therapeutic Support</h3>
          <p class="text-lg">Our team of specialists provides a range of therapeutic services, including speech therapy, occupational therapy, and counseling, to support students' overall development.</p>
        </div>
      </div>
  
      <div class="glass-bg p-8 rounded-xl shadow-lg mb-16">
        <h2 class="text-3xl font-semibold text-yellow-300 mb-6">Our Special Needs Programs</h2>
        <ul class="space-y-4">
          <li v-for="program in programs" :key="program.name" class="flex items-start">
            <span class="text-yellow-300 mr-4 mt-1 text-2xl">
              <i :class="program.icon"></i>
            </span>
            <div>
              <h4 class="text-xl font-semibold mb-2">{{ program.name }}</h4>
              <p>{{ program.description }}</p>
            </div>
          </li>
        </ul>
      </div>
  
      <div class="text-center">
        <h3 class="text-2xl font-semibold text-yellow-300 mb-4">Inclusive Education for All</h3>
        <p class="text-lg max-w-2xl mx-auto">At Schield Centre, we believe that every child deserves the opportunity to learn and grow in a supportive environment. Our special needs programs are designed to empower students, build confidence, and help them reach their full potential.</p>
      </div>
    </div>
  </div>
</template>

<script setup>
const programs = [
  {
    name: 'Learning Disabilities Program',
    icon: 'fas fa-brain',
    description: 'Tailored support for students with dyslexia, dyscalculia, and other learning differences.'
  },
  {
    name: 'Autism Spectrum Support',
    icon: 'fas fa-puzzle-piece',
    description: 'Specialized interventions and accommodations for students on the autism spectrum.'
  },
  {
    name: 'Physical and Sensory Needs',
    icon: 'fas fa-wheelchair',
    description: 'Accessible facilities and adaptive technologies for students with physical or sensory impairments.'
  },
  {
    name: 'Behavioral and Emotional Support',
    icon: 'fas fa-heart',
    description: 'Comprehensive support for students with behavioral or emotional challenges.'
  },
  {
    name: 'Speech and Language Therapy',
    icon: 'fas fa-volume-up',
    description: 'Dedicated sessions to improve speech and language skills through targeted therapy and exercises.'
  },
  {
    name: 'Occupational Therapy',
    icon: 'fas fa-hand-paper',
    description: 'Therapy focused on developing fine motor skills, sensory processing, and daily living activities.'
  },
  {
    name: 'Social Skills Training',
    icon: 'fas fa-users',
    description: 'Programs designed to enhance social interactions, communication, and teamwork skills in a supportive environment.'
  },
  {
    name: 'Assistive Technology Integration',
    icon: 'fas fa-laptop',
    description: 'Utilization of specialized technology to support learning and accessibility needs, including software and devices tailored to individual requirements.'
  },
  {
    name: 'Parent Training and Support',
    icon: 'fas fa-hands-helping',
    description: 'Workshops and resources for parents to better support their child’s needs and navigate available services and strategies.'
  },
  {
    name: 'Sensory Integration Activities',
    icon: 'fas fa-cogs',
    description: 'Activities designed to help children manage sensory processing issues and enhance sensory experiences in a structured setting.'
  }
]
</script>

<style scoped>
/* Glassy background style */
.glass-bg {
  background: rgba(255, 255, 255, 0.15);
  border: 1px solid rgba(255, 255, 255, 0.3);
  backdrop-filter: blur(12px);
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.4);
}

/* Apply styling to headings and paragraphs */
h1, h2, h3, h4, p {
  font-family: 'Nunito', sans-serif;
}

h1 {
  font-weight: 800;
}

h2 {
  font-weight: 700;
}

h3, h4 {
  font-weight: 600;
}

p {
  font-weight: 400;
}
</style>
