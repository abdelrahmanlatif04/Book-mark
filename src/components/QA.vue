<template>
  <div
    class="overflow-hidden text-start relative w-full border-b-[0.5px] px-1 py-[6px]"
    @click="showAnswer(i)"
  >
    <div
      class="question cursor-pointer relative before:right-2 before:aspect-square before:border-8 before:border-transparent before:border-t-white before:absolute before:top-0 before:translate-y-1/3 after:right-2 after:aspect-square after:border-8 after:border-transparent after:border-t-soft-blue after:-z-10 after:absolute after:top-0 after:translate-y-[45%]"
      :class="`${item.state ? 'text-soft-red' : 'text-black'}`"
    >
      {{ item.question }}
    </div>
    <div
      class="relative h-fit border-t-[0.5px] py-[6px] px-2 cursor-pointer before:right-2 before:aspect-square before:border-8 before:border-transparent before:border-b-white before:absolute before:top-0 before:translate-y-[61.666%] after:right-2 after:aspect-square after:border-8 after:border-transparent after:border-b-soft-red after:-z-10 after:absolute after:top-0 after:translate-y-1/2"
      :class="`${item.state ? 'block' : 'hidden'}`"
    >
      {{ item.answer }}
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {};
  },
  methods: {
    showAnswer() {
      this.$emit("showAnswer", this.item);
    },
  },
  props: ["item"],
};
</script>
