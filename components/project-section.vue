<template>
  <section class="flex justify-center bg-[#fff]" id="project">
    <div class="max-w-[1200px] m-auto w-[92%] mt-36">
      <div class="title text-center mb-[90px]">
        <h1
          class="text-4xl uppercase font-bold tracking-wide mb-8 after:content-[''] after:ml-2 after:bg-[#7843e9] after:h-[3px] after:w-[40px] after:block after:mt-3 after:absolute after:rounded-md after:left-1/2 after:-translate-x-1/2"
          ref="projectheading"
        >
          Projects
        </h1>
        <div class="info flex justify-center">
          <p
            class="text-md text-center text-[#555] w-[600px]"
            ref="projectparagraph"
          >
            Here you will find more information about me, what I do, and my
            current skills mostly in terms of programming and technology
          </p>
        </div>
      </div>
      <div class="projects">
        <div
          class="grid grid-cols-[1fr] md:grid-cols-[1.5fr_1fr] gap-[50px]"
          v-for="p in projects"
        >
          <div class="image" ref="image">
            <img :src="p.img" class="mt-[-100px] rotate-[0.8deg]" alt="" />
          </div>
          <div
            class="info m-[8rem_0_0_20px] max-lg:m-[2rem_0_0_20px] max-md:text-[16px] max-md:flex max-md:flex-col max-md:items-center max-md:text-center max-md:mb-[2rem] max-sm:mb-[3rem] max-md:m-[-90px_0_0_0]"
            ref="info"
          >
            <h2 class="text-[28px] font-bold mb-[20px]">{{ p.name }}</h2>
            <p
              class="text-[18px] text-[#666] max-w-[500px] leading-[1.7] mb-[30px]"
            >
              {{ p.description }}
            </p>
            <div class="btn mt-6">
              <NuxtLink
                class="bg-[#7843e9] text-white p-[15px_50px] cursor-pointer rounded-lg text-lg uppercase tracking-[1px]"
                target="_blank"
                :href="p.link"
                >Demo</NuxtLink
              >
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted, onBeforeUnmount } from "vue";
const projects = ref([
  {
    img: `/_nuxt/assets/Projects/1.png`,
    name: "Leo Template",
    description:
      "Leo is a successful Open-Source project that I createdb which have been featured on some of the biggest tech sites like CSS-Tricks, Hostinger, etc & used by thousands of developers globally",
    link: "https://aboulabed.github.io/Template-One/",
  },
  {
    img: `/_nuxt/assets/Projects/2.png`,
    name: "Kasper Template",
    description:
      "Kasper is a multiservice logistics and transport company and I created their website from scratch using the frontend tools I know.",
    link: "https://aboulabed.github.io/Template-Two/",
  },
  {
    img: `/_nuxt/assets/Projects/3.png`,
    name: "Template Three",
    description:
      "I re-created the frontend of Template Three's official web app because I got attracted to their beautiful UI. It was a great experience for me to build the entire frontend.",
    link: "https://aboulabed.github.io/Template-Three/",
  },
  {
    img: `/_nuxt/assets/Projects/4.png`,
    name: "Template Four",
    description:
      "Dashboard is a web template that I created targeting the restaurant and food industry which anyone can use to present their business online.",
    link: "https://aboulabed.github.io/Template-Four/",
  },
  {
    img: `/_nuxt/assets/Projects/5.png`,
    name: "Special Design",
    description:
      "Special is a successful Open-Source project that I createdb which have been featured on some of the biggest tech sites like CSS-Tricks, Hostinger, etc & used by thousands of developers globally",
    link: "https://aboulabed.github.io/Template-Five/",
  },
  {
    img: `/_nuxt/assets/Projects/6.png`,
    name: "Bondi Template",
    description:
      "Bondi is a multiservice logistics and transport company and I created their website from scratch using the frontend tools I know.",
    link: "https://aboulabed.github.io/Template-Six/",
  },
  {
    img: `/_nuxt/assets/Projects/7.png`,
    name: "Bliss Portofolio",
    description:
      "I re-created the frontend of Bliss's official web app because I got attracted to their beautiful UI. It was a great experience for me to build the entire frontend.",
    link: "https://aboulabed.github.io/Template-Seven/",
  },
  {
    img: `/_nuxt/assets/Projects/8.png`,
    name: "Unfold Template",
    description:
      "Unfold is a web template that I created targeting the restaurant and food industry which anyone can use to present their business online.",
    link: "https://aboulabed.github.io/Template-Eight/",
  },
  {
    img: `/_nuxt/assets/Projects/9.png`,
    name: "Photo Gallery",
    description:
      "Photo Gallery is a successful Open-Source project that I createdb which have been featured on some of the biggest tech sites like CSS-Tricks, Hostinger, etc & used by thousands of developers globally",
    link: "https://photogallery-umber.vercel.app/",
  },
  {
    img: `/_nuxt/assets/Projects/10.png`,
    name: "Nuxt Dojo",
    description:
      "Nuxt Dojo is a multiservice logistics and transport company and I created their website from scratch using the frontend tools I know.",
    link: "https://nuxt-dojo-gilt.vercel.app/products",
  },
  {
    img: `/_nuxt/assets/Projects/11.png`,
    name: "Vue Todo",
    description:
      "I re-created the frontend of Vue Todo's official web app because I got attracted to their beautiful UI. It was a great experience for me to build the entire frontend.",
    link: "https://vue-todo-ecru-nine.vercel.app/",
  },
  {
    img: `/_nuxt/assets/Projects/12.png`,
    name: "Repos Getter",
    description:
      "Repos Getter is a web template that I created targeting the restaurant and food industry which anyone can use to present their business online.",
    link: "https://aboulabed.github.io/Repos-Geter/",
  },
]);
const projectheading = ref(null);
const projectparagraph = ref(null);
const image = ref(null);
const info = ref(null);
let observer = null;

onMounted(() => {
  console.log(image.value, info.value);
  initIntersectionObserver();
});

onBeforeUnmount(() => {
  observer.disconnect();
});

function initIntersectionObserver() {
  observer = new IntersectionObserver((entries) => {
    entries.forEach((entry) => {
      if (entry.isIntersecting) {
        // The element is in view, start the animation

        projectheading.value.classList.add("animate");
        projectparagraph.value.classList.add("animate");
      }
    });
  });

  observer.observe(projectheading.value);
  observer.observe(projectparagraph.value);
}
</script>

<style scoped>
.title {
  h1.animate {
    opacity: 0;
    animation: slide-in-top 1.75s forwards;
  }
  p.animate {
    opacity: 0;
    animation: slide-in-top 1.5s forwards;
  }
}
</style>
