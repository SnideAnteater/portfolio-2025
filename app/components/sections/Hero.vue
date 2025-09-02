<template>
  <div
    class="hero min-h-screen flex items-center justify-center bg-gradient-to-br from-black via-gray-900 to-black overflow-hidden"
  >
    <div class="container mx-auto px-6 text-center">
      <div class="mb-8 animate-scale-in">
        <NuxtImg
          src="/images/selfpic.jpg"
          alt="Akmal's Image"
          width="200"
          height="400"
          class="object-top w-48 h-48 rounded-full mx-auto object-cover shadow-2xl ring-4 ring-gray-500/20 hover:ring-gray-400/40 transition-all duration-300 animate-float hover:scale-110 hover:rotate-3 transform-gpu"
        />
      </div>
      <div class="space-y-4 max-w-4xl mx-auto">
        <h1
          class="hero-title text-5xl md:text-7xl font-bold bg-gradient-to-r from-white to-gray-200 bg-clip-text text-transparent animate-slide-in-left opacity-0"
        >
          Hey! I'm Akmal
        </h1>
        <h2
          class="hero-title text-3xl md:text-5xl font-semibold text-gray-300 animate-slide-in-right opacity-0"
        >
          Software Engineer
        </h2>
        <p
          class="hero-description text-lg md:text-xl text-gray-400 leading-relaxed max-w-2xl mx-auto mt-6 animate-fade-in-up-delay-3"
        >
          A software engineer that is striving to become a Full Stack Developer.
          Has a knack for creating 3D websites and web applications.
        </p>

        <div class="flex flex-row gap-6 justify-center mt-8">
          <NuxtLink
            to="https://github.com/SnideAnteater"
            target="_blank"
            external
            class="relative items-center bg-gray-800/20 backdrop-blur-sm text-white font-semibold p-4 rounded-xl border border-gray-700/30 hover:border-gray-500/50 transition-all duration-300 group animate-fade-in-up-delay-4 opacity-0 hover:scale-125 hover:rotate-12 hover:-translate-y-3 transform-gpu"
          >
            <Icon
              name="uil:github"
              class="w-8 h-8 group-hover:text-purple-400 transition-colors"
            />
          </NuxtLink>

          <NuxtLink
            to="https://www.linkedin.com/in/akmalyassin/"
            target="_blank"
            external
            class="relative items-center bg-gray-800/20 backdrop-blur-sm text-white font-semibold p-4 rounded-xl border border-gray-700/30 hover:border-gray-500/50 transition-all duration-300 group animate-fade-in-up-delay-5 opacity-0 hover:scale-125 hover:rotate-12 hover:-translate-y-3 transform-gpu"
          >
            <Icon
              name="uil:linkedin"
              class="w-8 h-8 group-hover:text-blue-400 transition-colors"
            />
          </NuxtLink>
        </div>
        <div class="mt-12 animate-fade-in-up-delay-6 opacity-0">
          <NuxtLink
            to="/projects"
            class="inline-block bg-gradient-to-r from-purple-600 to-blue-600 hover:from-purple-700 hover:to-blue-700 text-white font-bold py-4 px-8 rounded-full shadow-lg hover:shadow-xl transition-all duration-300 transform hover:scale-105 hover:-translate-y-2 animate-glow-pulse"
          >
            View My Work
          </NuxtLink>
        </div>
      </div>
    </div>

    <div class="absolute inset-0 overflow-hidden pointer-events-none">
      <div
        class="absolute w-2 h-2 bg-purple-500/30 rounded-full animate-float-slow"
        style="top: 20%; left: 10%"
      ></div>
      <div
        class="absolute w-1 h-1 bg-blue-500/40 rounded-full animate-float-reverse"
        style="top: 60%; right: 15%"
      ></div>
      <div
        class="absolute w-3 h-3 bg-purple-400/20 rounded-full animate-float-delayed"
        style="bottom: 30%; left: 20%"
      ></div>
      <div
        class="absolute w-2 h-2 bg-gray-400/20 rounded-full animate-float"
        style="top: 80%; right: 30%"
      ></div>
    </div>
  </div>

  <About />
</template>

<script setup>
import { NuxtImg } from "#components";
import About from "./About.vue";
</script>

<style scoped>
.hero {
  position: relative;
}

.hero::before {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: radial-gradient(
    circle at 50% 50%,
    rgba(75, 85, 99, 0.1) 0%,
    transparent 50%
  );
  pointer-events: none;
}

.hero-title {
  background-size: 200% 100%;
}
</style>
