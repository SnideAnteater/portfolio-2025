<template>
  <div class="projects-page bg-black text-white min-h-screen py-20">
    <div class="container mx-auto px-6 max-w-7xl">
      <!-- Page Header -->
      <div class="text-center mb-20 animate-fade-in-up">
        <h1
          class="text-6xl md:text-7xl font-bold bg-gradient-to-r from-white to-gray-300 bg-clip-text text-transparent mb-6 animate-scale-in"
        >
          My Projects
        </h1>
        <div
          class="w-32 h-1 bg-gradient-to-r from-purple-500 to-blue-500 mx-auto rounded-full animate-expand-width animation-delay-400"
        ></div>
        <p
          class="text-xl text-gray-400 mt-8 max-w-3xl mx-auto animate-fade-in-up-delay-3"
        >
          A showcase of my personal and professional projects, demonstrating my
          skills in full-stack development, 3D web experiences, and interactive
          applications.
        </p>
      </div>

      <!-- Professional Projects Section -->
      <div class="mb-20">
        <h2
          class="text-4xl md:text-5xl font-bold text-center mb-16 animate-fade-in-up"
        >
          <span
            class="bg-gradient-to-r from-purple-400 to-blue-400 bg-clip-text text-transparent"
          >
            Professional Projects
          </span>
        </h2>

        <div class="grid lg:grid-cols-2 gap-12">
          <ProjectCard
            v-for="(project, index) in professionalProjects"
            :key="project.id"
            :project="project"
            :index="index"
            type="professional"
          />
        </div>
      </div>

      <!-- Personal Projects Section -->
      <div>
        <h2
          class="text-4xl md:text-5xl font-bold text-center mb-16 animate-fade-in-up"
        >
          <span
            class="bg-gradient-to-r from-green-400 to-cyan-400 bg-clip-text text-transparent"
          >
            Personal Projects
          </span>
        </h2>

        <div class="grid lg:grid-cols-2 gap-12">
          <ProjectCard
            v-for="(project, index) in personalProjects"
            :key="project.id"
            :project="project"
            :index="index"
            type="personal"
          />
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
        class="absolute w-3 h-3 bg-green-500/15 rounded-full animate-float-delayed"
        style="bottom: 20%; left: 15%"
      ></div>
      <div
        class="absolute w-2 h-2 bg-cyan-500/20 rounded-full animate-float"
        style="top: 40%; right: 5%"
      ></div>
    </div>
  </div>
</template>

<script setup>
import ProjectCard from "~/components/ProjectCard.vue";
// Professional Projects Data
const professionalProjects = [
  {
    id: 1,
    name: "Healthmetrics Dashboard",
    description:
      "Comprehensive healthcare management dashboard built with .NET and Angular. Features include patient management, invoice generation (MyInvois), and integrated payment gateway (Curlec). Includes real-time data visualization and responsive design.",
    technologies: [".NET", "AngularJS", "C#", "SQL Server"],
    images: [
      "/images/projects/hms/hmsDashboard.png",
      "/images/projects/hms/hmsDashboard2.png",
    ],
    liveUrl: null,
    githubUrl: null,
    company: "Healthmetrics",
  },
  {
    id: 2,
    name: "Meet Ecobear",
    description:
      "Interactive AR experience that allows users to meet and interact with a virtual bear character in a real-world environment.",
    technologies: ["JavaScript", "A-Frame", "8th Wall", "Geolocation API"],
    images: ["/images/projects/cravefx/ecobear.jpeg"],
    liveUrl:
      "https://www.linkedin.com/posts/cravefx_maketheswitch-design-animation-activity-7062384599296872448-_An9?utm_source=share&utm_medium=member_desktop&rcm=ACoAACbCAfoBoV8w4GNFkmYER0HNYiiWRaVLfSY",
    githubUrl: null,
    company: "CraveFx",
  },
  {
    id: 3,
    name: "Sleigh Stacker",
    description:
      "Christmas-themed game built with Unity. Players stack presents on a sleigh while avoiding obstacles.",
    technologies: ["C#", "Unity"],
    images: [
      "/images/projects/cravefx/sleigh1.jpeg",
      "/images/projects/cravefx/sleigh2.jpeg",
      "/images/projects/cravefx/sleigh3.jpeg",
    ],
    liveUrl:
      "https://www.linkedin.com/feed/update/urn:li:activity:7011961792276955136?utm_source=share&utm_medium=member_desktop&rcm=ACoAACbCAfoBoV8w4GNFkmYER0HNYiiWRaVLfSY",
    githubUrl: null,
    company: "CraveFx",
  },
  {
    id: 4,
    name: "West Coast Expressway Mobile App",
    description:
      "Comprehensive mobile application for West Coast Expressway featuring real-time road feed. Built with Ionic Cordova",
    technologies: ["AngularJS", "Ionic Cordova", ".NET", "Microsoft SQL"],
    images: [
      "/images/projects/recogine/wce1.webp",
      "/images/projects/recogine/wce2.webp",
      "/images/projects/recogine/wce3.webp",
    ],
    liveUrl: null,
    githubUrl: null,
    company: "Recogine Technologies",
  },
];

// Personal Projects Data
const personalProjects = [
  {
    id: 5,
    name: "UDP Packets with NodeJs",
    description:
      "Sending and Receive UDP packets from a client to a server using NodeJs. It is to be used with Unreal Engine",
    technologies: ["NodeJs"],
    images: [],
    liveUrl: null,
    githubUrl: "https://github.com/SnideAnteater/UDPPackets_NodeJS",
  },
  {
    id: 6,
    name: "Train Simulator",
    description:
      "Train simulator created with NextJs. Uses Djistra algorithm to find the shortest path of the task",
    technologies: ["NextJs", "React", "TypeScript"],
    images: [],
    liveUrl: "https://train-simulator.vercel.app/",
    githubUrl: "https://github.com/SnideAnteater/train_simulator",
  },
  {
    id: 7,
    name: "Limb Tracker",
    description:
      "Real-time limb tracking application using computer vision and machine learning. Built with modern web technologies and TensorFlow.js.",
    technologies: ["Javascript", "Tensorflow"],
    images: [],
    liveUrl: null,
    githubUrl: "https://github.com/SnideAnteater/tensorflow-javascript",
  },
  {
    id: 8,
    name: "Image Tracker with A-Frame",
    description:
      "Augmented reality image tracking application built with A-Frame. Allows users to place 3D models in the real world using image markers.",
    technologies: ["A-Frame", "JavaScript", "WebXR"],
    images: [],
    liveUrl: null,
    githubUrl: "https://github.com/SnideAnteater/image-tracking-aframe",
  },
];

// SEO Meta
useSeoMeta({
  title: "Projects - Akmal Yassin | Full Stack Developer",
  description:
    "Explore my professional and personal projects showcasing full-stack development, 3D web experiences, and interactive applications.",
  ogTitle: "Projects - Akmal Yassin",
  ogDescription:
    "Professional and personal projects by Akmal Yassin - Full Stack Developer",
});
</script>

<style scoped>
.projects-page {
  position: relative;
}

.projects-page::before {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: radial-gradient(
      circle at 25% 25%,
      rgba(139, 92, 246, 0.03) 0%,
      transparent 50%
    ),
    radial-gradient(
      circle at 75% 75%,
      rgba(59, 130, 246, 0.03) 0%,
      transparent 50%
    );
  pointer-events: none;
}
</style>
