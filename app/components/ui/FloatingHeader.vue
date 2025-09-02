<template>
  <div
    class="fixed top-6 left-1/2 transform -translate-x-1/2 z-50 transition-all duration-300"
    :class="{
      'translate-y-0 opacity-100': isVisible,
      '-translate-y-full opacity-0': !isVisible,
    }"
  >
    <nav
      class="bg-black/70 backdrop-blur-md border border-gray-700/50 rounded-full px-6 py-3 shadow-2xl"
    >
      <div class="flex items-center space-x-6">
        <NuxtLink
          to="/"
          :class="[
            'px-4 py-2 rounded-full text-sm font-medium transition-all duration-300',
            activeTab === 'home'
              ? 'bg-white text-black shadow-lg'
              : 'text-gray-300 hover:text-white hover:bg-gray-800/50',
          ]"
          @click="setActiveTab('home')"
        >
          Home
        </NuxtLink>

        <div class="w-px h-6 bg-gray-600"></div>

        <NuxtLink
          to="/projects"
          :class="[
            'px-4 py-2 rounded-full text-sm font-medium transition-all duration-300',
            activeTab === 'projects'
              ? 'bg-white text-black shadow-lg'
              : 'text-gray-300 hover:text-white hover:bg-gray-800/50',
          ]"
          @click="setActiveTab('projects')"
        >
          Projects
        </NuxtLink>
      </div>
    </nav>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted, watchEffect } from "vue";
import { useRoute } from "vue-router";

const isVisible = ref(true);
const activeTab = ref("home");
const route = useRoute();

// Set active tab based on current route
watchEffect(() => {
  if (route.path === "/") {
    activeTab.value = "home";
  } else if (route.path.includes("projects")) {
    activeTab.value = "projects";
  }
});

const setActiveTab = (tab) => {
  activeTab.value = tab;
};

// Handle scroll behavior
let lastScrollY = 0;

const handleScroll = () => {
  const currentScrollY = window.scrollY;

  // Show header when scrolling up or at top, hide when scrolling down
  if (currentScrollY < lastScrollY || currentScrollY < 100) {
    isVisible.value = true;
  } else {
    isVisible.value = false;
  }

  lastScrollY = currentScrollY;
};

onMounted(() => {
  window.addEventListener("scroll", handleScroll, { passive: true });
});

onUnmounted(() => {
  window.removeEventListener("scroll", handleScroll);
});
</script>

<style scoped>
/* Additional custom styles if needed */
.backdrop-blur-md {
  backdrop-filter: blur(12px);
}
</style>
