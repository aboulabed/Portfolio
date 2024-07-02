<template>
  <section class="flex justify-center bg-[#fafafa]" id="contact">
    <div class="max-w-[1200px] m-auto w-[92%] mt-36 flex items-center flex-col">
      <div class="title text-center mb-[50px]">
        <h1
          class="text-4xl uppercase font-bold tracking-wide mb-8 after:content-[''] after:ml-2 after:bg-[#7843e9] after:h-[3px] after:w-[40px] after:block after:mt-3 after:absolute after:rounded-md after:left-1/2 after:-translate-x-1/2"
          ref="contactheading"
        >
          Contact
        </h1>
        <div class="info flex justify-center">
          <p class="text-lg text-center text-[#555]" ref="contactparagraph">
            Feel free to Contact me by submitting the form below and I will get
            back to you as soon as possible
          </p>
        </div>
      </div>
      <div
        class="form mb-36 rounded p-[40px] bg-[white] max-w-[800px] w-[95%] m-[50px_auto_0_auto] shadow-[#64646f33]"
      >
        <form action="" class="form flex items-center flex-col">
          <div class="name mb-8 w-[100%]">
            <label
              for="name"
              class="color: #666; text-[14px] spacing-1; font-bold mb-2 block text-left"
              >Name</label
            >
            <input
              ref="name"
              class="text-[#333] p-[20px] w-[100%] text-[16px] bg-[#f0f0f0] rounded font-semibold"
              type="text"
              name="name"
              placeholder="Enter Your Name"
            />
          </div>
          <div class="email mb-8 w-[100%]">
            <label
              for="email"
              class="color: #666; text-[14px] spacing-1; font-bold mb-2 block text-left"
              >Email</label
            >
            <input
              class="text-[#333] p-[20px] w-[100%] text-[16px] bg-[#f0f0f0] rounded font-semibold"
              type="email"
              name="email"
              placeholder="Enter Your Email"
            />
          </div>
          <div class="message mb-8 w-[100%]">
            <label
              for="message"
              class="color: #666; text-[14px] spacing-1; font-bold mb-2 block text-left"
              >Message</label
            >
            <textarea
              ref="message"
              class="text-[#333] p-[20px] w-[100%] text-[16px] bg-[#f0f0f0] rounded font-semibold"
              name="message"
              placeholder="Enter Your Message"
              style="resize: none"
              required=""
              cols="30"
              rows="10"
            ></textarea>
          </div>

          <input
            class="bg-[#7843e9] self-end text-white p-[20px_60px] cursor-pointer rounded-lg text-md uppercase tracking-[1px] font-semibold"
            type="submit"
            value="Submit"
            @click="sendEmail()"
          />
        </form>
      </div>
    </div>
  </section>
</template>

<script setup>
const contactheading = ref(null);
const contactparagraph = ref(null);
const name = ref(null);
const message = ref(null);
const sendEmail = () => {
  // Replace 'example@example.com' with the recipient's email address
  window.location.href = `mailto:suhailattackontitanahmed@gmail.com?subject=${name.value.value}&body=${message.value.value}`;
};
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
        contactheading.value.classList.add("animate");
        contactparagraph.value.classList.add("animate");
      }
    });
  });

  observer.observe(contactheading.value);
  observer.observe(contactparagraph.value);
}
</script>

<style scoped>
section {
  background: linear-gradient(
      to right,
      rgba(245, 245, 245, 0.8),
      rgba(245, 245, 245, 0.8)
    ),
    url("@/assets/common-bg.svg");
}

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
