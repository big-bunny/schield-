<template>
  <div class="min-h-screen bg-gradient-to-t from-indigo-950 via-indigo-900 to-purple-700 text-white py-16">
    <div class="container mx-auto px-4">
      <h1 class="text-5xl font-extrabold text-center mb-12 animate-fadeIn text-shadow-lg">Schield Gallery</h1>

      <!-- Tabs -->
      <div class="mb-8">
        <div class="flex justify-center space-x-4">
          <button 
            v-for="tab in tabs" 
            :key="tab"
            @click="activeTab = tab"
            :class="['px-4 py-2 rounded-lg transition-colors duration-300', 
                     activeTab === tab ? 'bg-yellow-300 text-indigo-900' : 'bg-indigo-800 hover:bg-indigo-700']"
          >
            {{ tab }}
          </button>
        </div>
      </div>

      <!-- Albums -->
      <div v-if="activeTab !== 'All'" class="mb-8">
        <div class="flex flex-wrap justify-center gap-4">
          <button 
            v-for="album in currentAlbums" 
            :key="album"
            @click="activeAlbum = album"
            :class="['px-4 py-2 rounded-lg transition-colors duration-300', 
                     activeAlbum === album ? 'bg-yellow-300 text-indigo-900' : 'bg-indigo-800 hover:bg-indigo-700']"
          >
            {{ album }}
          </button>
        </div>
      </div>

      <!-- Gallery Grid -->
      <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-6">
        <div 
          v-for="item in filteredGalleryItems" 
          :key="item.id" 
          @click="openModal(item)"
          class="bg-indigo-800 rounded-xl overflow-hidden shadow-lg hover:shadow-2xl transition-shadow duration-300 cursor-pointer"
        >
          <div v-if="item.type === 'image'" class="aspect-w-16 aspect-h-9">
            <img :src="item.src" :alt="item.title" class="object-cover w-full h-full">
          </div>
          <div v-else-if="item.type === 'video'" class="aspect-w-16 aspect-h-9">
            <video :src="item.src" class="object-cover w-full h-full"></video>
          </div>
          <div class="p-4">
            <h3 class="text-lg font-semibold mb-2">{{ item.title }}</h3>
            <p class="text-sm text-gray-300">{{ item.album }}</p>
          </div>
        </div>
      </div>
    </div>

    <!-- Modal -->
    <Transition name="fade">
      <div v-if="selectedItem" class="fixed inset-0 bg-black bg-opacity-75 flex items-center justify-center z-50" @click.self="closeModal">
        <div class="max-w-4xl w-full bg-indigo-900 rounded-lg overflow-hidden shadow-2xl">
          <div class="relative">
            <img v-if="selectedItem.type === 'image'" :src="selectedItem.src" :alt="selectedItem.title" class="w-full h-auto" ref="mediaElement">
            <video v-else-if="selectedItem.type === 'video'" :src="selectedItem.src" class="w-full h-auto" controls ref="mediaElement"></video>
            
            <!-- Control buttons -->
            <div class="absolute bottom-4 left-4 right-4 flex justify-center space-x-4">
              <button @click="zoomIn" class="bg-indigo-600 hover:bg-indigo-700 text-white font-bold py-2 px-4 rounded">
                Zoom In
              </button>
              <button @click="zoomOut" class="bg-indigo-600 hover:bg-indigo-700 text-white font-bold py-2 px-4 rounded">
                Zoom Out
              </button>
              <button v-if="selectedItem.type === 'video'" @click="togglePlay" class="bg-indigo-600 hover:bg-indigo-700 text-white font-bold py-2 px-4 rounded">
                {{ isPlaying ? 'Pause' : 'Play' }}
              </button>
              <button @click="toggleFullscreen" class="bg-indigo-600 hover:bg-indigo-700 text-white font-bold py-2 px-4 rounded">
                {{ isFullscreen ? 'Exit Fullscreen' : 'Fullscreen' }}
              </button>
            </div>
          </div>
          <div class="p-4">
            <h2 class="text-2xl font-bold mb-2">{{ selectedItem.title }}</h2>
            <p class="text-gray-300">{{ selectedItem.album }}</p>
          </div>
        </div>
      </div>
    </Transition>
  </div>
</template>

<script setup>
import { ref, computed, watch } from 'vue'

const tabs = ['All', 'Images', 'Videos']
const activeTab = ref('All')
const activeAlbum = ref('')
const selectedItem = ref(null)
const mediaElement = ref(null)
const isPlaying = ref(false)
const isFullscreen = ref(false)
const zoomLevel = ref(1)

// Function to get file extension
const getFileExtension = (filename) => {
  return filename.split('.').pop().toLowerCase()
}

// Function to determine if a file is an image
const isImage = (filename) => {
  const imageExtensions = ['jpg', 'jpeg', 'png', 'gif', 'svg']
  return imageExtensions.includes(getFileExtension(filename))
}

// Function to determine if a file is a video
const isVideo = (filename) => {
  const videoExtensions = ['mp4', 'avi', 'mkv', 'mov']
  return videoExtensions.includes(getFileExtension(filename))
}

// Import all media files
const mediaFiles = import.meta.glob([
  '/public/**/*.{jpg,jpeg,png,gif,svg,mp4,avi,mkv,mov}',
  '/src/assets/**/*.{jpg,jpeg,png,gif,svg,mp4,avi,mkv,mov}'
], { eager: true })

// Create gallery items from imported files
const galleryItems = Object.entries(mediaFiles).map(([path, module]) => {
  const filename = path.split('/').pop()
  const type = isImage(filename) ? 'image' : 'video'
  const album = path.split('/').slice(-2, -1)[0]
  
  return {
    id: path,
    type,
    src: module.default,
    title: filename,
    album
  }
})

// Compute unique albums
const uniqueAlbums = computed(() => {
  const albums = new Set(galleryItems.map(item => item.album))
  return Array.from(albums)
})

// Compute current albums based on active tab
const currentAlbums = computed(() => {
  if (activeTab.value === 'All') return uniqueAlbums.value
  return uniqueAlbums.value.filter(album => 
    galleryItems.some(item => item.album === album && 
      (activeTab.value === 'Images' ? item.type === 'image' : item.type === 'video')
    )
  )
})

// Filter gallery items based on active tab and album
const filteredGalleryItems = computed(() => {
  let items = galleryItems
  if (activeTab.value !== 'All') {
    items = items.filter(item => 
      activeTab.value === 'Images' ? item.type === 'image' : item.type === 'video'
    )
  }
  if (activeAlbum.value) {
    items = items.filter(item => item.album === activeAlbum.value)
  }
  return items
})

const openModal = (item) => {
  selectedItem.value = item
  zoomLevel.value = 1
  isPlaying.value = false
  isFullscreen.value = false
}

const closeModal = () => {
  selectedItem.value = null
}

const zoomIn = () => {
  zoomLevel.value = Math.min(zoomLevel.value + 0.1, 3)
  applyZoom()
}

const zoomOut = () => {
  zoomLevel.value = Math.max(zoomLevel.value - 0.1, 0.5)
  applyZoom()
}

const applyZoom = () => {
  if (mediaElement.value) {
    mediaElement.value.style.transform = `scale(${zoomLevel.value})`
  }
}

const togglePlay = () => {
  if (mediaElement.value) {
    if (isPlaying.value) {
      mediaElement.value.pause()
    } else {
      mediaElement.value.play()
    }
    isPlaying.value = !isPlaying.value
  }
}

const toggleFullscreen = () => {
  if (!document.fullscreenElement) {
    mediaElement.value.requestFullscreen()
    isFullscreen.value = true
  } else {
    document.exitFullscreen()
    isFullscreen.value = false
  }
}

// Reset active album when changing tabs
watch(activeTab, () => {
  activeAlbum.value = ''
})
</script>

<style scoped>
@keyframes fadeIn {
  from { opacity: 0; }
  to { opacity: 1; }
}

.animate-fadeIn {
  animation: fadeIn 1s ease-out;
}

.text-shadow-lg {
  text-shadow: 2px 2px 10px rgba(0, 0, 0, 0.5);
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.3s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}

/* Add smooth transition for zoom */
img, video {
  transition: transform 0.3s ease;
}
</style>