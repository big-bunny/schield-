<template>
  <header class="bg-gradient-to-r from-purple-600 to-indigo-600 text-white sticky top-0 z-50 animate-fadeIn">
    <div class="container mx-auto px-6 py-4 flex items-center">
      <!-- Branding Section -->
      <div class="flex-1 flex justify-start">
        <NuxtLink
          to="/"
          class="text-3xl font-bold hover:text-yellow-300 transition-all duration-300 transform hover:scale-105"
        >
          Schield Centre
        </NuxtLink>
      </div>

      <!-- Navigation Links Section -->
      <nav class="flex-1 flex justify-center">
        <ul class="flex space-x-4">
          <li v-for="item in navItems" :key="item.to">
            <NuxtLink
              :to="item.to"
              class="nav-button text-lg px-4 py-2 rounded-full bg-indigo-700 hover:bg-yellow-300 hover:text-indigo-800 transition-all duration-300 transform hover:scale-110 hover:shadow-lg inline-block flex items-center space-x-2"
            >
            <UIcon  :name="item.icon" class="w-8 h-8" />
              <span>{{ item.text }}</span>
            </NuxtLink>
          </li>
        </ul>
      </nav>

      <!-- Location Button Section -->
      <div class="flex-1 flex justify-end">
        <a
          href="https://www.google.com/maps/search/?api=1&query=Schield+Centre,+Kajiado,+Kenya"
          target="_blank"
          class="map-button text-yellow-300 hover:text-indigo-800 hover:bg-yellow-300 flex items-center space-x-2 px-4 py-2 rounded-full transition-all duration-300 transform hover:scale-105"
        >
          <UIcon name="i-mdi-map-marker" class="animate-bounce w-8 h-8" />
          <span class="hidden sm:inline">Kajiado, Kenya</span>
        </a>
      </div>
    </div>
  </header>
</template>

<script setup>
const navItems = [
  { to: '/', text: 'Home', icon: 'i-heroicons-outline-home' },
  { to: '/cbc', text: 'CBC', icon: 'i-heroicons-outline-academic-cap' },
  { to: '/jss', text: 'JSS', icon: 'i-heroicons-outline-book-open' },
  { to: '/toto', text: 'Schield Toto', icon: 'i-heroicons-outline-sparkles' },
  { to: '/team', text: 'Team', icon: 'i-heroicons-outline-sparkles' },
  { to: '/special-needs', text: 'Special Needs', icon: 'i-heroicons-outline-heart' },
  { to: '/gallery', text: 'Gallery', icon: 'i-heroicons-outline-mail' },
]
</script>
<style scoped>
@keyframes fadeIn {
  from { opacity: 0; }
  to { opacity: 1; }
}

.animate-fadeIn {
  animation: fadeIn 1s ease-out;
}

.nav-button, .map-button {
  position: relative;
  overflow: hidden;
}

.nav-button::after, .map-button::after {
  content: '';
  position: absolute;
  top: 50%;
  left: 50%;
  width: 5px;
  height: 5px;
  background: rgba(255, 255, 255, 0.5);
  opacity: 0;
  border-radius: 100%;
  transform: scale(1, 1) translate(-50%);
  transform-origin: 50% 50%;
}

@keyframes ripple {
  0% {
    transform: scale(0, 0);
    opacity: 1;
  }
  20% {
    transform: scale(25, 25);
    opacity: 1;
  }
  100% {
    opacity: 0;
    transform: scale(40, 40);
  }
}

.nav-button:focus:not(:active)::after, .map-button:focus:not(:active)::after {
  animation: ripple 1s ease-out;
}

@keyframes bounce {
  0%, 100% {
    transform: translateY(-25%);
    animation-timing-function: cubic-bezier(0.8, 0, 1, 1);
  }
  50% {
    transform: translateY(0);
    animation-timing-function: cubic-bezier(0, 0, 0.2, 1);
  }
}

.animate-bounce {
  animation: bounce 1s infinite;
}

.sticky { position: sticky; }
.top-0 { top: 0; }
.z-50 { z-index: 50; }
</style>
