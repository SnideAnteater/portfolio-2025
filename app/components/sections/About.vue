<template>
  <div class="about-section bg-black text-white py-20 overflow-hidden">
    <div class="container mx-auto px-6 max-w-7xl">
      <div class="mb-20">
        <!-- About Me Section Header -->
        <div class="text-center mb-16 animate-fade-in-up">
          <h2
            class="text-5xl md:text-6xl font-bold bg-gradient-to-r from-white to-gray-300 bg-clip-text text-transparent mb-6 animate-scale-in"
          >
            About Me
          </h2>
          <div
            class="w-24 h-1 bg-gradient-to-r from-gray-500 to-gray-700 mx-auto rounded-full animate-expand-width animation-delay-400"
          ></div>
        </div>

        <!-- About Content Grid -->
        <div class="grid md:grid-cols-2 gap-12 items-center">
          <!-- Description Text -->
          <div class="space-y-6 animate-slide-in-left">
            <p
              class="text-lg leading-relaxed text-gray-300 animate-fade-in-up-delay-3"
            >
              Results-driven
              <span class="text-white font-semibold shimmer-bg animate-shimmer"
                >Senior Interactive Developer</span
              >
              with a proven track record in crafting engaging and innovative web
              solutions. I specialize in developing interactive websites and
              experiences that push the boundaries of what's possible on the
              web.
            </p>
            <p
              class="text-lg leading-relaxed text-gray-300 animate-fade-in-up-delay-4"
            >
              Beyond frontend development, I've shaped backend operations
              including cloud services deployment, mobile app development for
              both Play Store and App Store, and comprehensive project
              management through GitHub repositories and documentation.
            </p>
          </div>

          <!-- Skills Grid with Enhanced Animations -->
          <div
            class="grid grid-cols-2 sm:grid-cols-3 gap-4 animate-slide-in-right"
          >
            <div
              v-for="(skill, index) in skills"
              :key="skill"
              :class="`skill-card bg-gray-900 hover:bg-gray-800 px-4 py-3 rounded-lg text-center transition-all duration-300 border border-gray-700 cursor-pointer animate-skill-${
                index + 1
              } hover:scale-110 hover:-translate-y-2 hover:rotate-3 transform-gpu animate-bounce-gentle`"
            >
              <span class="text-sm font-medium text-gray-200">{{ skill }}</span>
            </div>
          </div>
        </div>
      </div>

      <!-- Experience Section -->
      <div>
        <!-- Experience Header -->
        <div class="text-center mb-16 animate-fade-in-up">
          <h2
            class="text-5xl md:text-6xl font-bold bg-gradient-to-r from-white to-gray-300 bg-clip-text text-transparent mb-6 animate-scale-in"
          >
            Experience
          </h2>
          <div
            class="w-24 h-1 bg-gradient-to-r from-gray-500 to-gray-700 mx-auto rounded-full animate-expand-width animation-delay-400"
          ></div>
        </div>

        <!-- Experience Cards -->
        <div class="space-y-8">
          <div
            v-for="(experience, index) in experiences"
            :key="index"
            :class="`relative experience-card bg-gray-900 p-8 rounded-xl border border-gray-700 hover:border-gray-600 transition-all duration-500 group overflow-hidden animate-experience-${
              index + 1
            } hover:scale-105 hover:-translate-y-3 hover:shadow-2xl transform-gpu animate-float`"
            :style="`animation-delay: ${index * 0.2 + 0.8}s`"
          >
            <!-- Animated background gradient -->
            <div
              class="absolute inset-0 bg-gradient-to-r from-purple-900/5 to-blue-900/5 opacity-0 group-hover:opacity-100 transition-opacity duration-500 shimmer-bg animate-shimmer"
            ></div>

            <div
              class="relative z-10 flex flex-col md:flex-row md:items-center justify-between mb-4"
            >
              <div class="flex-1">
                <NuxtImg
                  :src="experience.imgsrc || experience.imagesrc"
                  :alt="experience.company + ' logo'"
                  class="object-contain w-48 h-20 mb-4 animate-scale-in-bounce hover:scale-110 hover:rotate-6 transition-all duration-300 transform-gpu"
                  width="100"
                />
                <h3
                  class="text-2xl font-bold text-white mb-2 w-full animate-slide-in-left"
                >
                  {{ experience.position }}
                </h3>
                <h4
                  class="text-xl text-gray-300 mb-2 animate-slide-in-left animation-delay-200"
                >
                  {{ experience.company }}
                </h4>
              </div>
              <div
                class="bg-gray-800 px-4 py-2 rounded-full duration-badge animate-scale-in-bounce hover:scale-110 hover:bg-gray-700 transition-all duration-300 animate-glow-pulse"
              >
                <span class="text-sm font-medium text-gray-200">{{
                  experience.duration
                }}</span>
              </div>
            </div>
            <p
              class="relative z-10 text-gray-400 leading-relaxed animate-fade-in-up animation-delay-600"
              v-html="experience.description"
            ></p>
          </div>
        </div>
      </div>
    </div>

    <!-- Floating background elements -->
    <div class="absolute inset-0 overflow-hidden pointer-events-none">
      <div
        class="absolute w-2 h-2 bg-purple-500/20 rounded-full animate-float-slow"
        style="top: 10%; left: 5%"
      ></div>
      <div
        class="absolute w-1 h-1 bg-blue-500/30 rounded-full animate-float-reverse"
        style="top: 70%; right: 10%"
      ></div>
      <div
        class="absolute w-3 h-3 bg-gray-500/10 rounded-full animate-float-delayed"
        style="bottom: 20%; left: 15%"
      ></div>
    </div>
  </div>
</template>

<script setup lang="ts">
const skills = [
  "C++",
  "C#",
  "TypeScript",
  "JavaScript",
  "Python",
  "Node.js",
  "React.js",
  "Angular.js",
  ".NET",
  "HTML5",
  "CSS3",
  "Vue",
];

const experiences = [
  {
    position: "Senior Software Engineer",
    company: "Healthmetrics",
    duration: "Jan 2025 - Present",
    description:
      "Full stack developer working with .NET, AngularJs, NextJS with React and C++<br>Created a prototype design website using FumaDocs for the company design bible for a more comprehensive guideline on how to design for the company<br>Created a prototype Nextjs project that can be connected to the company's .NET backend to replace Angular<br>Delivered MyInvois and Payment Gateway(Curlec) features using .NET and Angular<br>Worked on the production database to find out bugs that were reported and fixed them",
    imgsrc: "/images/HMSLogo.png",
  },
  {
    position: "Software Engineer",
    company: "CraveFx",
    duration: "April 2022 - Dec 2024",
    description:
      "Mainly work with frameworks like Javascript, React Typescript, CSS, HTML, C#, C++, Python, Nodejs, PHP.<br>Handle backend data with MySQL and MongoDB<br>Lead and build the interactive team foundation<br>Code Documentation, Research and Development, and Tutorials all documented in Notion<br>Participate in discussions with clients to understand the requirements and technical specifications for the product.<br>Establish effective pipelines and guides to integrate assets for artists.<br>Collaborate with directors, artists, designers, and programmers to understand how to best utilize existing tools and technology.<br>Support regular project reviews to recommend schedule changes, cost or resource adjustments.<br>Mentor and guide junior developers and interns to elevate the overall technical capabilities of the entire development team<br>Actively engage in collaboration and delegate tasks among developers to optimize efficiency and ensure project completion within designated timelines.<br>Build a 3D interactive website for a client that supports multiple languages and sets a specific language based on the user's location<br>Built and assisted with developing a web game that lets users explore Singapore by using an Otter which they can then collect trophies and vouchers that can be claimed in real life.<br>Build numerous Instagram, Facebook and Tiktok filters that have garnered thousands of views.<br>Assisted in integrating 3D model with animation into client's existing websites",
    imagesrc: "/images/CraveFx.png",
  },
  {
    position: "Junior Software Engineer",
    company: "Recogine Technologies",
    duration: "Jan 2021 - April 2022",
    description: `Mainly work with AngularJS, Javascript, C#, .NET <br>Handle backend data with Microsoft SQL <br> Lead the design of highway app for West Coast Expressway <br> Developed a mobile app for West Coast Expressway using AngularJS with Ionic Cordova which supports navigation from multiple points using a map system, bus location tracking and bus arrival estimation. <br> Build a CRUD backend service using .NET framework to communicate Microsoft SQL and mobile app`,
    imagesrc: "/images/RecogineTechnology.jpg",
  },
];
</script>

<style scoped>
.about-section {
  position: relative;
}

.about-section::before {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: radial-gradient(
      circle at 30% 20%,
      rgba(75, 85, 99, 0.05) 0%,
      transparent 50%
    ),
    radial-gradient(
      circle at 70% 80%,
      rgba(75, 85, 99, 0.05) 0%,
      transparent 50%
    );
  pointer-events: none;
}

.skill-card {
  transform-origin: center;
  will-change: transform;
}

.skill-card:hover {
  box-shadow: 0 10px 25px rgba(139, 92, 246, 0.2);
}

.experience-card {
  transform-origin: center;
  will-change: transform;
  background-size: 200% 100%;
}

.experience-card:hover {
  background: linear-gradient(135deg, #111827 0%, #1f2937 100%);
}

.duration-badge {
  will-change: transform, background-color, box-shadow;
}

.animation-delay-200 {
  animation-delay: 0.2s;
}

.animation-delay-400 {
  animation-delay: 0.4s;
}

.animation-delay-600 {
  animation-delay: 0.6s;
}
</style>
