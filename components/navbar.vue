<template>
  <nav class="shadow-[0_10px_100px_rgba(0,0,0,0.1)] fixed w-full bg-white z-10">
    <div
      class="nav-content h-[70px] max-lg:text-sm max-lg:p-[0_2rem] text-lg flex justify-between p-[1rem_5rem]"
    >
      <div
        class="flex items-center hover:text-[#7843e9] duration-300 cursor-pointer text-[#333]"
      >
        <div class="img">
          <img src="../assets/logo.png" alt="logo" class="w-[40px] h-[40px]" />
        </div>
        <h2 class="ml-3 font-bold uppercase">Suhail Ahmed</h2>
      </div>
      <div class="list flex items-center max-sm:hidden">
        <ul class="flex font-semibold gap-10">
          <li
            v-for="l in list"
            class="duration-300 hover:text-[#7843e9] cursor-pointer"
          >
            <NuxtLink :href="l.link">{{ l.name }}</NuxtLink>
          </li>
        </ul>
      </div>
      <div class="header-toggle sm:hidden flex items-center">
        <v-icon
          icon="mdi-view-headline"
          v-show="showList"
          @click="toggleShowList()"
        />
        <v-icon icon="mdi-close" v-show="!showList" @click="toggleShowList()" />
      </div>
    </div>
    <div class="mobile-list sm:hidden" v-show="!showList">
      <div class="list">
        <ul class="flex flex-col font-semibold">
          <li
            v-for="l in list"
            class="duration-300 border-t border-solid border-t-[#eee] text-end hover:text-[#7843e9] cursor-pointer p-[1.5rem_3rem] w-full"
          >
            <NuxtLink :href="l.link">{{ l.name }}</NuxtLink>
          </li>
        </ul>
      </div>
    </div>
  </nav>
</template>

<script setup>
const list = ref([
  { name: "Home", link: "./" },
  { name: "About", link: "#about" },
  { name: "Projects", link: "" },
  { name: "Contact", link: "" },
]);
const showList = ref(true);
const toggleShowList = () => {
  showList.value = !showList.value;
};
</script>

<style scoped></style>
