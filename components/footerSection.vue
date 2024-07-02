<template>
  <footer class="bg-black text-white py-20 flex justify-center">
    <div class="container">
      <div
        class="upper max-sm:flex-col max-md:text-center max-md:items-center mb-20 flex justify-between"
      >
        <div class="left max-md:mb-7 max-w-[500px] w-[40%]" ref="footerLeft">
          <h2 class="uppercase text-xl mb-4 font-bold">Suhail Ahmed</h2>
          <p class="text-[15px]">
            A Frontend focused Web Developer building the Frontend of Websites
            and Web Applications that leads to the success of the overall
            product
          </p>
        </div>
        <div class="right" ref="footerRight">
          <h2 class="uppercase text-xl mb-4 font-bold">Social</h2>
          <div class="social-medias flex">
            <NuxtLink
              class="mr-1"
              v-for="socialMedia in socialMedias"
              :to="socialMedia.link"
              target="_blank"
              ><v-icon>{{ socialMedia.icon }}</v-icon></NuxtLink
            >
          </div>
        </div>
      </div>
      <hr class="border border-solid border-t-[#444_!important]" />
      <div class="lower mt-10 text-center" ref="footerLower">
        <p>
          © Copyright <span>{{ year }}</span> . Made by
          <NuxtLink to="/" target="_blank" class="underline font-bold"
            >Suhail Ahmed</NuxtLink
          >
        </p>
      </div>
    </div>
  </footer>
</template>

<script setup>
const socialMedias = ref([
  {
    link: "https://www.linkedin.com/in/suhail-ahmed-2b290230b/",
    icon: "mdi-linkedin",
  },
  {
    link: "https://www.facebook.com/profile.php?id=100071937310430",
    icon: "mdi-facebook",
  },
  {
    link: "https://github.com/aboulabed",
    icon: "mdi-github",
  },
  {
    link: "https://x.com/SAbwlabd",
    icon: "mdi-twitter",
  },
  {
    link: "https://www.instagram.com/suhail_ahmed246/",
    icon: "mdi-instagram",
  },
]);
const footerLeft = ref(null);
const footerRight = ref(null);
const footerLower = ref(null);
const d = new Date();
const year = d.getFullYear();
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
        footerLeft.value.classList.add("animate");
        footerRight.value.classList.add("animate");
        footerLower.value.classList.add("animate");
      }
    });
  });

  observer.observe(footerLeft.value);
  observer.observe(footerRight.value);
  observer.observe(footerLower.value);
}
</script>

<style scoped>
.left.animate {
  animation: slide-in-left 2s forwards;
}
.right.animate {
  animation: slide-in-right 2s forwards;
}
.lower.animate {
  animation: slide-in-bottom 2s forwards;
}
</style>
