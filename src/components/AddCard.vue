<template>
  <div
    class="flex border-t bg-white mx-auto items-center flex-col gap-7 w-[280px]] overflow-hidden text-center pt-10 pb-5 rounded-xl shadow-md transition duration-300 hover:shadow-xl hover:scale-[1.05] cursor-pointer"
  >
    <img :src="img" :alt="`${browser}'s logo`" />
    <div>
      <div class="title text-xl">Add to {{ browser }}</div>
      <div class="my-1 text-sm text-grayish-blue">
        Minimum version {{ version }}
      </div>
    </div>
    <img src="../assets/bg-dots.svg" class="" />
    <button
      class="bg-soft-blue w-60 text-white py-2 px-7 rounded-md hover:bg-transparent hover:text-soft-blue hover:shadow-none border-soft-blue border-2 shadow-md smooth"
    >
      Add & Install Extension
    </button>
  </div>
</template>

<script>
export default {
  data() {
    return {};
  },
  props: ["img","browser", "version"],
};
</script>
