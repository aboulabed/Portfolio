<template>
  <section class="flex justify-center bg-[#fafafa]" id="about">
    <div class="max-w-[1200px] m-auto w-[92%] mt-36">
      <div class="title text-center mb-[90px]">
        <h1
          class="text-4xl uppercase font-bold tracking-wide mb-8 after:content-[''] after:ml-2 after:bg-[#7843e9] after:h-[3px] after:w-[40px] after:block after:mt-3 after:absolute after:rounded-md after:left-1/2 after:-translate-x-1/2"
          ref="aboutheading"
        >
          About Me
        </h1>
        <div class="info flex justify-center">
          <p
            class="text-md text-center text-[#555] w-[600px]"
            ref="aboutparagraph"
          >
            Here you will find more information about me, what I do, and my
            current skills mostly in terms of programming and technology
          </p>
        </div>
      </div>
      <div class="about mt-5 mb-12 grid gap-[100px] grid-cols-[1fr_1fr]">
        <div class="left" ref="left">
          <h3 class="font-bold text-[1.75rem] mb-6">Get to know me!</h3>
          <div class="info max-w-[600px]">
            <p class="text-[18px] text-[#666] mb-[10px]">
              I'm a <strong>Frontend Focused Web Developer</strong> building and
              managing the Front-end of Websites and Web Applications that leads
              to the success of the overall product. Check out some of my work
              in the <strong>Projects</strong> section.
            </p>
            <p class="text-[18px] text-[#666] mb-[10px]">
              I also like sharing content related to the stuff that I have
              learned over the years in <strong>Web Development</strong> so it
              can help other people of the Dev Community. Feel free to Connect
              or Follow me on my
              <NuxtLink
                to="https://www.linkedin.com/in/suhail-ahmed-2b290230b/"
                target="_blank"
                class="text-[#7843e9] font-bold decoration-[#7843e9] underline m-[0_3px"
                >Linkedin</NuxtLink
              >
              and
              <NuxtLink
                to="https://www.instagram.com/suhail_ahmed246/"
                target="_blank"
                class="text-[#7843e9] font-bold decoration-[#7843e9] underline m-[0_3px]"
                >Instagram</NuxtLink
              >
              where I post useful content related to Web Development and
              Programming
            </p>
            <p class="text-[18px] text-[#666] mb-[10px]">
              I'm open to <strong>Job</strong> opportunities where I can
              contribute, learn and grow. If you have a good opportunity that
              matches my skills and experience then don't hesitate to
              <strong>contact</strong> me.
            </p>
          </div>
          <div class="btn w-0 text-center mt-14">
            <NuxtLink
              class="bg-[#7843e9] text-white p-[15px_50px] cursor-pointer rounded-sm text-[14px] uppercase tracking-[1px] font-bold"
              >Contact</NuxtLink
            >
          </div>
        </div>
        <div class="right" ref="right">
          <h3 class="font-bold text-[1.75rem] mb-6">My Skills</h3>
          <div class="skills flex flex-wrap">
            <p
              class="w-fit text-[#666] m-[0_15px_15px_0] duration-300 hover:text-white hover:scale-110 hover:rotate-[1deg] hover:bg-[#7843e9] p-[10px_20px] bg-[#99999933] rounded-[5px] text-[16px] font-medium"
              v-for="skill in skills"
            >
              {{ skill }}
            </p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted, onBeforeUnmount } from "vue";

const left = ref(null);
const right = ref(null);
const aboutheading = ref(null);
const aboutparagraph = ref(null);
let observer = null;

onMounted(() => {
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
        left.value.classList.add("animate");
        right.value.classList.add("animate");
        aboutheading.value.classList.add("animate");
        aboutparagraph.value.classList.add("animate");
      }
    });
  });

  observer.observe(left.value);
}
const skills = ref([
  "HTML",
  "CSS",
  "JavaScript",
  "VueJS",
  "NuxtJS",
  "GIT",
  "Github",
  "Responsive Design",
  "TailwindCSS",
  "Bootstrap",
  "Vuetify",
  "Api",
]);
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
.about {
  @media (max-width: 900px) {
    grid-template-columns: 1fr;
    gap: 80px;
  }

  .left.animate {
    opacity: 0;
    transform: translateX(-1000px);
    animation: slide-in-left 2s cubic-bezier(0.25, 0.46, 0.45, 0.94) both;
  }
  .right.animate {
    opacity: 0;
    transform: translateX(-1000px);
    animation: slide-in-right 2s cubic-bezier(0.25, 0.46, 0.45, 0.94) both;
  }
}

@keyframes mainFadeIn {
  0% {
    opacity: 0;
  }
  100% {
    opacity: 1;
  }
}
@keyframes secFadeIn {
  0% {
    opacity: 0;
  }
  100% {
    opacity: 0.8;
  }
}

@keyframes slide-in-left {
  0% {
    -webkit-transform: translateX(-1000px);
    transform: translateX(-1000px);
    opacity: 0;
  }
  100% {
    -webkit-transform: translateX(0);
    transform: translateX(0);
    opacity: 1;
  }
}
@keyframes slide-in-right {
  0% {
    -webkit-transform: translateX(1000px);
    transform: translateX(1000px);
    opacity: 0;
  }
  100% {
    -webkit-transform: translateX(0);
    transform: translateX(0);
    opacity: 1;
  }
}
@keyframes slide-in-top {
  0% {
    -webkit-transform: translateY(-1000px);
    transform: translateY(-1000px);
    opacity: 0;
  }
  100% {
    -webkit-transform: translateY(0);
    transform: translateY(0);
    opacity: 1;
  }
}
</style>
