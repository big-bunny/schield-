<template>
  <div class="min-h-screen bg-gradient-to-br from-purple-950 to-indigo-950 text-white py-16">
    <div class="container mx-auto px-4">
      <h1 class="text-5xl font-bold text-center mb-12 text-yellow-300 font-extrabold">Schield Toto (Kindergarten)</h1>
      
      <p class="text-xl text-center mb-12 max-w-3xl mx-auto font-semibold">At Schield Toto, we create a safe and nurturing environment for our youngest learners. Our Kindergarten program focuses on foundational skills in literacy, numeracy, and social interaction.</p>
      
      <div class="grid grid-cols-1 md:grid-cols-2 gap-12 mb-16">
        <div class="glass-bg p-8 rounded-xl shadow-lg transform hover:scale-105 transition-all duration-300">
          <h3 class="text-2xl font-semibold text-yellow-300 mb-4">Play-Based Learning</h3>
          <p class="text-lg">We believe that children learn best through play. Our curriculum includes a variety of play-based activities that encourage exploration and discovery.</p>
        </div>
        <div class="glass-bg p-8 rounded-xl shadow-lg transform hover:scale-105 transition-all duration-300">
          <h3 class="text-2xl font-semibold text-yellow-300 mb-4">Safe Environment</h3>
          <p class="text-lg">Our facilities are designed to be safe and welcoming for young children, with a focus on security and comfort.</p>
        </div>
      </div>
  
      <div class="glass-bg p-8 rounded-xl shadow-lg mb-16">
        <h2 class="text-3xl font-semibold text-yellow-300 mb-6">Our Kindergarten Approach</h2>
        <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
          <div v-for="approach in approaches" :key="approach.title" class="text-center">
            <span class="text-4xl text-yellow-300 mb-4 block">
              <i :class="approach.icon"></i>
            </span>
            <h4 class="text-xl font-semibold mb-2">{{ approach.title }}</h4>
            <p class="text-lg">{{ approach.description }}</p>
          </div>
        </div>
      </div>

      <div class="glass-bg p-8 rounded-xl shadow-lg mb-16">
        <h2 class="text-3xl font-semibold text-yellow-300 mb-6">Programs & Activities</h2>
        <ul class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
          <li v-for="program in programs" :key="program.id" class="text-center">
            <img :src="program.image" alt="Program Image" class="w-full h-32 object-cover mb-4 rounded-md shadow-md" />
            <h4 class="text-xl font-semibold text-yellow-300 mb-2">{{ program.title }}</h4>
            <p class="text-lg">{{ program.description }}</p>
          </li>
        </ul>
      </div>

      <div class="text-center">
        <h3 class="text-2xl font-semibold text-yellow-300 mb-4">Nurturing Young Minds</h3>
        <p class="text-lg max-w-2xl mx-auto">At Schield Toto, we understand that early childhood education lays the foundation for lifelong learning. Our program is designed to spark curiosity, foster creativity, and build confidence in every child.</p>
      </div>
    </div>
  </div>
</template>

<script setup>
const approaches = [
  {
    title: 'Holistic Development',
    icon: 'fas fa-child',
    description: 'We focus on cognitive, social, emotional, and physical development to ensure well-rounded growth.'
  },
  {
    title: 'Language Rich Environment',
    icon: 'fas fa-comments',
    description: 'We provide a language-rich setting to enhance communication skills and early literacy.'
  },
  {
    title: 'Creative Expression',
    icon: 'fas fa-palette',
    description: 'Through art, music, and dramatic play, we encourage children to express themselves creatively.'
  }
]

const programs = [
  {
    id: 1,
    title: 'Science Exploration',
    description: 'Hands-on experiments and activities to introduce basic scientific concepts and foster curiosity about the natural world.',
    image: '/images/gallery/field-trip.jpg',
  },
  {
    id: 2,
    title: 'Outdoor Adventures',
    description: 'Activities in our safe, spacious outdoor areas help children develop physical skills and an appreciation for nature.',
    image: '/images/gallery/community/playground.jpg',
  },
  {
    id: 3,
    title: 'Music and Movement',
    description: 'Children engage in musical activities and movement games that enhance coordination and rhythm while having fun.',
    image: '/images/programs/music.jpg',
  },
  {
    id: 4,
    title: 'Art and Craft',
    description: 'Creative projects that allow children to explore various art materials and express their creativity through painting, drawing, and crafting.',
    image: '/images/programs/art.jpg',
  },
  {
    id: 5,
    title: 'Story Time',
    description: 'Interactive storytelling sessions that promote language development, imagination, and a love for books.',
    image: '/images/programs/athletics.jpg',
  },
  {
    id: 6,
    title: 'Physical Education',
    description: 'Games and exercises that help develop gross motor skills, coordination, and encourage healthy physical activity.',
    image: '/images/programs/schield1.jpg',
  },
  {
    id: 7,
    title: 'Social Skills Development',
    description: 'Activities and group games that teach children essential social skills, including sharing, cooperation, and empathy.',
    image: '/gallery/community/community1.jpg',
  },
  {
    id: 8,
    title: 'Language Enrichment',
    description: 'Programs that focus on building vocabulary, language comprehension, and communication skills through interactive play.',
    image: '/gallery/community/community2.jpg',
   },
   { id: 9,
    
    title: 'Cultural Awareness',
    description: 'Introducing children to diverse cultures through stories, music, and activities that promote respect and understanding of different traditions.',
    image: '/gallery/aware.jpg',

  },
  {
    id: 10,
    title: 'Parent Involvement',
    description: 'Regular events and activities that encourage parents to participate in their child’s learning journey, strengthening the home-school connection.',
    image: '/gallery/invlove.jpg',
  },
]
</script>

<style scoped>
/* Glassy background style */
.glass-bg {
  background: rgba(255, 255, 255, 0.2);
  border: 1px solid rgba(255, 255, 255, 0.3);
  backdrop-filter: blur(10px);
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.3);
}

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
