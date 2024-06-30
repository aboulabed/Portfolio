<template>
  <section class="flex justify-center relative">
    <div class="heading box content-center flex flex-wrap justify-center">
      <div class="heading mb-7 title w-full justify-center flex">
        
        <h1
          class="text-6xl max-sm:text-5xl max-sm:w-[450px] mb-5 max-sm:leading-[3.5rem] uppercase text-center font-bold tracking-[1px]"
        >
          Hey, I'm Suhail Ahmed <span></span>
        </h1>
      </div>

      <div class="info role m-12 max-sm:m-20 max-w-[45rem] text-center">
        
        <p
          class="text-xl text-[#333] max-sm:text-[18px] w-full leading-[2.20rem]"
        >
          A Result-Oriented Web Developer building and managing Websites and Web
          Applications that leads to the success of the overall product
        </p>
      </div>
      <div class="btn w-full text-center mt-6">
        <NuxtLink
          class="bg-[#7843e9] text-white p-[20px_75px] cursor-pointer rounded-lg text-xl uppercase tracking-[1px] font-bold"
          >Projects</NuxtLink
        >
      </div>
    </div>
    <div
      class="social-media hidden lg:block p-[6px] z-10 bg-white absolute left-0 top-1/2 translate-y-[-50%]"
    >
      <div
        v-for="socialMedia in socialMedias"
        class="p-[10px] hover:bg-[rgba(120,67,233,0.2)] duration-300 rounded-[4px]"
        :class="socialMedia.name"
      >
        <NuxtLink :to="socialMedia.link" target="_blank"
          ><v-icon>{{ socialMedia.icon }}</v-icon></NuxtLink
        >
      </div>
    </div>
    <div class="center absolute hidden sm:block" @click="scrollToAbout()">
      <svg width="40" height="90" viewBox="0 0 50 130">
        <rect
          id="scroll"
          x="0"
          y="5"
          rx="25"
          ry="25"
          width="50"
          height="70"
          stroke="#333"
          fill="#FFF"
          stroke-width="4"
        ></rect>
        <circle id="circle--shape" cx="25" cy="32" r="8" fill="#333"></circle>
      </svg>
    </div>
  </section>
</template>

<script setup>
const socialMedias = ref([
  {
    name: "linkedin",
    link: "https://www.linkedin.com/in/suhail-ahmed-2b290230b/",
    icon: "mdi-linkedin",
  },
  {
    name: "facebook",
    link: "https://www.facebook.com/profile.php?id=100071937310430",
    icon: "mdi-facebook",
  },
  {
    name: "github",
    link: "https://github.com/aboulabed",
    icon: "mdi-github",
  },
  {
    name: "twitter",
    link: "https://x.com/SAbwlabd",
    icon: "mdi-twitter",
  },
  {
    name: "instagram",
    link: "https://www.instagram.com/suhail_ahmed246/",
    icon: "mdi-instagram",
  },
]);
</script>

<style scoped>
section {
  background: linear-gradient(
      to right,
      rgba(245, 245, 245, 0.8),
      rgba(245, 245, 245, 0.8)
    ),
    url("@/assets/common-bg.svg");

  .box .title {
    width: 100%;
    position: relative;
    display: flex;
    align-items: center;
    height: 50px;
  }
  .box .title .block {
    width: 0%;
    height: inherit;
    background: #ffb510;
    position: absolute;
    animation: mainBlock 2s cubic-bezier(0.74, 0.06, 0.4, 0.92) forwards;
    display: flex;
  }
  .box .title h1 {
    -webkit-animation: mainFadeIn 2s forwards;
    -o-animation: mainFadeIn 2s forwards;
    animation: mainFadeIn 2s forwards;
    animation-delay: 1.6s;
    opacity: 0;
    display: flex;
    align-items: baseline;
    position: relative;
  }
  .box .title h1 span {
    width: 0px;
    height: 0px;
    -webkit-border-radius: 50%;
    -moz-border-radius: 50%;
    border-radius: 50%;
    background: #ffb510;
    -webkit-animation: load 0.6s cubic-bezier(0.74, 0.06, 0.4, 0.92) forwards;
    animation: popIn 0.8s cubic-bezier(0.74, 0.06, 0.4, 0.92) forwards;
    animation-delay: 2s;
    margin-left: 5px;
    margin-top: -10px;
    position: absolute;
    bottom: 13px;
    right: -12px;
  }
  .box .role {
    width: 100%;
    position: relative;
    display: flex;
    align-items: center;
    height: 30px;
  }
  .box .role .block {
    width: 0%;
    height: inherit;
    background: #e91e63;
    position: absolute;
    animation: secBlock 2s cubic-bezier(0.74, 0.06, 0.4, 0.92) forwards;
    animation-delay: 2s;
    display: flex;
  }
  .box .role p {
    animation: secFadeIn 2s forwards;
    animation-delay: 3.2s;
    opacity: 0;
  }

  .btn {
    animation: myAnim 2s ease 0s 1 normal forwards;
  }
  .social-media {
    animation: slide-in-left 2s cubic-bezier(0.25, 0.46, 0.45, 0.94) both;
  }
  .center {
    position: absolute;
    top: 90%;
    left: 50%;
    transform: translateX(-50%);
  }

  #scroll {
    animation: animateHeight 1.4s linear 0.3s 4;
    animation-iteration-count: infinite;
  }

  #circle--shape {
    animation: animateShape 1.6s ease-in-out 4;
    animation-iteration-count: infinite;
  }
}
@keyframes myAnim {
  0% {
    animation-timing-function: ease-in;
    opacity: 0;
    transform: translateY(250px);
  }

  38% {
    animation-timing-function: ease-out;
    opacity: 1;
    transform: translateY(0);
  }

  55% {
    animation-timing-function: ease-in;
    transform: translateY(65px);
  }

  72% {
    animation-timing-function: ease-out;
    transform: translateY(0);
  }

  81% {
    animation-timing-function: ease-in;
    transform: translateY(28px);
  }

  90% {
    animation-timing-function: ease-out;
    transform: translateY(0);
  }

  95% {
    animation-timing-function: ease-in;
    transform: translateY(8px);
  }

  100% {
    animation-timing-function: ease-out;
    transform: translateY(0);
  }
}
@keyframes mainBlock {
  0% {
    width: 0%;
    left: 0;
  }
  50% {
    width: 100%;
    left: 0;
  }
  100% {
    width: 0;
    left: 100%;
  }
}
@keyframes secBlock {
  0% {
    width: 0%;
    left: 0;
  }
  50% {
    width: 100%;
    left: 0;
  }
  100% {
    width: 0;
    left: 100%;
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
@keyframes popIn {
  0% {
    width: 0px;
    height: 0px;
    background: #e9d856;
    border: 0px solid #ddd;
    opacity: 0;
  }
  50% {
    width: 10px;
    height: 10px;
    background: #e9d856;
    opacity: 1;
    bottom: 45px;
  }
  65% {
    width: 7px;
    height: 7px;
    bottom: 0px;
    width: 15px;
  }
  80% {
    width: 10px;
    height: 10px;
    bottom: 20px;
  }
  100% {
    width: 7px;
    height: 7px;
    background: #e9d856;
    border: 0px solid #222;
    bottom: 13px;
  }
}
@keyframes secFadeIn {
  0% {
    opacity: 0;
  }
  100% {
    opacity: 0.5;
  }
}

@keyframes top {
  0% {
    opacity: 0;
    bottom: -80px;
  }
  100% {
    opacity: 1;
    bottom: 0px;
  }
}
@keyframes icon {
  0% {
    opacity: 0;
    transform: scale(0);
  }
  50% {
    opacity: 1;
    transform: scale(1.3) rotate(-2deg);
  }
  100% {
    opacity: 1;
    bottom: 0px;
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
    transform: translateY(-50%);
    opacity: 1;
  }
}
@keyframes animateShape {
  50% {
    cy: 70;
    opacity: 0.1;
  }
}
@keyframes animateHeight {
  70% {
    height: 90px;
  }
}
</style>
