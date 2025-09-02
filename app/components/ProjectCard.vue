<template>
  <div
    :class="`project-card bg-gray-900 rounded-2xl overflow-hidden border border-gray-700 hover:border-gray-600 transition-all duration-500 group animate-fade-in-rotate-${
      index % 2 === 0 ? 'left' : 'right'
    } hover:scale-105 hover:-translate-y-2 transform-gpu`"
    :style="`animation-delay: ${index * 0.2}s`"
  >
    <!-- Image Carousel -->
    <div
      class="relative h-64 md:h-80 overflow-hidden"
      v-if="project.images.length > 0"
    >
      <div class="carousel-container relative w-full h-full">
        <div
          class="carousel-track flex transition-transform duration-500 ease-in-out h-full"
          :style="`transform: translateX(-${currentImageIndex * 100}%)`"
        >
          <div
            v-for="(image, imgIndex) in project.images"
            :key="imgIndex"
            class="carousel-slide w-full h-full flex-shrink-0 relative"
          >
            <NuxtImg
              :src="image"
              :alt="`${project.name} screenshot ${imgIndex + 1}`"
              class="w-full h-full object-cover group-hover:scale-110 transition-transform duration-700"
              width="600"
              height="400"
            />
            <div
              class="absolute inset-0 bg-gradient-to-t from-black/50 to-transparent opacity-0 group-hover:opacity-100 transition-opacity duration-300"
            ></div>
          </div>
        </div>

        <!-- Carousel Navigation -->
        <div
          class="absolute bottom-4 left-1/2 transform -translate-x-1/2 flex space-x-2 z-10"
        >
          <button
            v-for="(image, imgIndex) in project.images"
            :key="imgIndex"
            @click="currentImageIndex = imgIndex"
            :class="`w-2 h-2 rounded-full transition-all duration-300 ${
              currentImageIndex === imgIndex
                ? 'bg-white scale-125'
                : 'bg-white/50 hover:bg-white/75'
            }`"
          ></button>
        </div>

        <!-- Navigation Arrows -->
        <button
          @click="previousImage"
          class="absolute left-4 top-1/2 transform -translate-y-1/2 bg-black/50 hover:bg-black/75 text-white p-2 rounded-full opacity-0 group-hover:opacity-100 transition-all duration-300 z-10"
        >
          <Icon name="heroicons:chevron-left" class="w-5 h-5" />
        </button>
        <button
          @click="nextImage"
          class="absolute right-4 top-1/2 transform -translate-y-1/2 bg-black/50 hover:bg-black/75 text-white p-2 rounded-full opacity-0 group-hover:opacity-100 transition-all duration-300 z-10"
        >
          <Icon name="heroicons:chevron-right" class="w-5 h-5" />
        </button>

        <!-- Project Type Badge -->
        <div
          :class="`absolute top-4 right-4 px-3 py-1 rounded-full text-xs font-semibold ${
            type === 'professional'
              ? 'bg-purple-600 text-white'
              : 'bg-green-600 text-white'
          } animate-scale-in-bounce`"
          :style="`animation-delay: ${index * 0.2 + 0.3}s`"
        >
          {{ type === "professional" ? "Professional" : "Personal" }}
        </div>
      </div>
    </div>

    <!-- Project Content -->
    <div class="p-6 space-y-4">
      <!-- Project Title -->
      <div class="flex items-start justify-between">
        <h3
          class="text-2xl font-bold text-white group-hover:text-transparent group-hover:bg-gradient-to-r group-hover:from-purple-400 group-hover:to-blue-400 group-hover:bg-clip-text transition-all duration-300 animate-slide-in-left"
        >
          {{ project.name }}
        </h3>
        <div
          v-if="project.company"
          class="text-sm text-gray-400 animate-fade-in-up-delay-2"
        >
          {{ project.company }}
        </div>
      </div>

      <!-- Description -->
      <p
        class="text-gray-300 leading-relaxed text-sm animate-fade-in-up-delay-3"
      >
        {{ project.description }}
      </p>

      <!-- Technologies -->
      <div class="animate-fade-in-up-delay-4">
        <h4 class="text-sm font-semibold text-gray-400 mb-3">
          Technologies Used:
        </h4>
        <div class="flex flex-wrap gap-2">
          <span
            v-for="(tech, techIndex) in project.technologies"
            :key="tech"
            :class="`inline-block px-3 py-1 bg-gray-800 text-gray-200 rounded-full text-xs font-medium hover:bg-gray-700 transition-colors duration-300 animate-scale-in-bounce`"
            :style="`animation-delay: ${index * 0.2 + techIndex * 0.1 + 0.5}s`"
          >
            {{ tech }}
          </span>
        </div>
      </div>

      <div class="flex space-x-4 pt-4 animate-fade-in-up-delay-5">
        <NuxtLink
          v-if="project.liveUrl"
          :to="project.liveUrl"
          target="_blank"
          external
          class="flex items-center space-x-2 bg-gradient-to-r from-purple-600 to-blue-600 hover:from-purple-700 hover:to-blue-700 text-white px-4 py-2 rounded-lg text-sm font-semibold transition-all duration-300 hover:scale-105 hover:-translate-y-1 transform-gpu"
        >
          <Icon name="heroicons:eye" class="w-4 h-4" />
          <span>Article Post</span>
        </NuxtLink>

        <NuxtLink
          v-if="project.githubUrl"
          :to="project.githubUrl"
          target="_blank"
          external
          class="flex items-center space-x-2 bg-gray-700 hover:bg-gray-600 text-white px-4 py-2 rounded-lg text-sm font-semibold transition-all duration-300 hover:scale-105 hover:-translate-y-1 transform-gpu"
        >
          <Icon name="uil:github" class="w-4 h-4" />
          <span>View Code</span>
        </NuxtLink>

        <div
          v-if="!project.liveUrl && !project.githubUrl"
          class="flex items-center space-x-2 bg-gray-800 text-gray-400 px-4 py-2 rounded-lg text-sm"
        >
          <Icon name="heroicons:lock-closed" class="w-4 h-4" />
          <span>Private Project</span>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
const props = defineProps({
  project: Object,
  index: Number,
  type: String,
});

const currentImageIndex = ref(0);

const nextImage = () => {
  currentImageIndex.value =
    (currentImageIndex.value + 1) % props.project.images.length;
};

const previousImage = () => {
  currentImageIndex.value =
    currentImageIndex.value === 0
      ? props.project.images.length - 1
      : currentImageIndex.value - 1;
};

// Auto-rotate images every 5 seconds
let autoRotateInterval = null;

onMounted(() => {
  autoRotateInterval = setInterval(() => {
    nextImage();
  }, 5000);
});

onUnmounted(() => {
  if (autoRotateInterval) {
    clearInterval(autoRotateInterval);
  }
});
</script>

<style scoped>
.project-card {
  transform-origin: center;
  will-change: transform;
}

.carousel-container {
  overflow: hidden;
}

.carousel-track {
  will-change: transform;
}

.carousel-slide {
  flex-shrink: 0;
}
</style>
