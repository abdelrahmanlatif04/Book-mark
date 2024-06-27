<template>
  <div
    class="cursor-pointer text-start relative w-full border-b-[0.5px] px-1"
    @click="showAnswer(i)"
  >
    <div
      class="question relative py-2 text-black"
      :class="`${item.state ? 'before:rotate-180' : ''}`"
    >
      {{ item.question }}
    </div>
    <div
      class="border-t-[0.5px] p-2 text-soft-blue font-semibold"
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

<style>
.question::before {
  content: url("../assets/icon-arrow.svg");
  @apply -translate-x-1/2 right-0 absolute top-1/2 -translate-y-1/2;
}
</style>
