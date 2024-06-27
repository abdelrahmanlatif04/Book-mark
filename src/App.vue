// TODO: change theme (dark & light) // TODO: ad
<template>
  <div class="flex flex-col lg:pt-10 gap-y-12">

    <nav class="flex justify-between">
      <a href="#hero"><img src="./assets/logo-bookmark.svg" alt="Logo" /> </a>
      <ul class="w-1/2 justify-evenly items-center px-5">
        <li><a href="#features">FEATURES</a></li>
        <li><a href="#pricing">PRICING</a></li>
        <li><a href="#contact">CONTACT</a></li>
        <li>
          <button
            class="bg-soft-red border-soft-red border-2 hover:bg-transparent hover:text-soft-red text-white py-1 px-6 rounded-md"
          >
            LOGIN
          </button>
        </li>
      </ul>
    </nav>
    <section id="hero" class="flex">
      <div class="flex flex-col justify-center gap-10">
        <div class="title text-5xl">A Simple Bookmark Manager</div>
        <div class="text-grayish-blue text-xl">
          A clean and simple interface to organize your favourite websites. Open
          a new browser tab and see your sites load instantly. Try it for free.
        </div>
        <div class="flex w-2/3 gap-5">
          <button
            class="bg-soft-blue shadow-sm smooth border-2 border-soft-blue text-white rounded-md py-2 px-6 hover:bg-transparent hover:text-soft-blue hover:shadow-soft-blue"
          >
            Get it on Chrome
          </button>
          <button
            class="bg-grayish-blue shadow-sm smooth border-2 text-white border-grayish-blue rounded-md py-2 px-6 hover:bg-transparent hover:text-grayish-blue hover:shadow-grayish-blue"
          >
            Get it on Firefox
          </button>
        </div>
      </div>
      <img
        src="./assets/illustration-hero.svg"
        alt="Main photo"
        class="w-2/3"
      />
    </section>

    <section id="features" class="flex flex-col gap-8 items-center">
      <div class="title text-center text-5xl">Features</div>
      <div class="text-center text-lg w-7/12">
        Our aim is to make it quick and easy for you to access your favourite
        websites. Your bookmarks sync between your devices so you can access
        them on the go.
      </div>
      <ul
        class="w-1/2 justify-evenly relative before:w-full before:absolute before:h-[0.5px] before:bg-grayish-blue before:-bottom-4"
      >
        <li
          class="text-center relative before:absolute px-2 before:rounded-xl before:-bottom-[18px] before:transition before:duration-300 smooth before:h-1 before:bg-blue-500 cursor-pointer"
          :class="
            features.current == i
              ? 'before:w-full before:left-0'
              : 'before:w-0 before:left-1/2'
          "
          v-for="(item, i) in features.tabs"
          :key="item"
          @click="features.current = i"
        >
          {{ item.navigator }}
        </li>
      </ul>
      <ul>
        <li
          class="flex justify-between"
          v-for="(item, i) in features.tabs"
          v-show="features.current == i"
          :key="item"
        >
          <img
            :src="`./src/assets/illustration-features-tab-${i + 1}.svg`"
            class="w-[48%]"
          />
          <div class="flex flex-col items-start w-[48%] justify-center gap-6">
            <div class="title text-4xl">{{ item.title }}</div>
            <div class="text-xl">{{ item.description }}</div>
            <button
              class="bg-soft-blue text-white rounded-lg py-2 px-5 hover:bg-transparent hover:text-soft-blue hover:shadow-none border-soft-blue border-2"
            >
              More Info
            </button>
          </div>
        </li>
      </ul>
    </section>

    <section id="pricing" class="text-center flex flex-col gap-8 items-center">
      <div class="title text-4xl">Download the extension</div>
      <div class="text-center text-lg w-7/12">
        We’ve got more browsers in the pipeline. Please do let us know if you’ve
        got a favourite you’d like us to prioritize.
      </div>

      <div class="flex justify-between flex-wrap gap-5">
        <add-card
          v-for="browser in browsers"
          :key="browser"
          :browser="browser.name"
          :version="browser.version"
        />
      </div>

      <div class="title text-4xl mt-5">Frequently Asked Questions</div>
      <div class="w-7/12 text-xl">
        Here are some of our FAQs. If you have any other questions you’d like
        answered please feel free to email us.
      </div>
      <div id="questions" class="w-1/2 border-t">
        <QA
          @showAnswer="showAnswer"
          v-for="question in QA"
          :key="question"
          :item="question"
        />
      </div>
      <button
        class="bg-soft-blue text-white rounded-lg py-2 px-5 hover:bg-transparent hover:text-soft-blue hover:shadow-none border-soft-blue border-2"
      >
        More Info
      </button>
    </section>

    <div>
      <section
        id="contact"
        class="text-center bg-soft-blue text-white py-10 px-[35%] flex flex-col gap-5"
      >
        <div class="text-sm tracking-[.5em]">35,000+ ALREADY JOINED</div>
        <div class="font-semibold text-3xl px-2">Stay up-to-date with what we’re doing</div>
        <form class="flex justify-center gap-4">
          <input
            class="text-start text-black focus:outline-none w-4/5 pl-3 focus:border-black focus:border rounded-md"
            type="email"
            placeholder="Enter your email address"
          />
          <button type="submit" class="bg-soft-red text-white px-4 py-2 w-2/5 rounded-md">
            Contact Us
          </button>
        </form>
      </section>
      <footer class="bg-dark-blue text-white flex justify-between pt-10 pb-8">
        <ul class="justify-between w-[45%]">
          <li>
            <img
              src="./assets/logo-bookmark-footer.svg"
              alt="Logo"
            />
          </li>
          <li><a href="#features">FEATURES</a></li>
          <li><a href="#pricing">PRICING</a></li>
          <li><a href="#contact">CONTACT</a></li>
        </ul>
        <ul class="gap-5 items-center">
          <li><img class="cursor-pointer" src="./assets/icon-facebook.svg" alt="facebook" /></li>
          <li><img class="cursor-pointer" src="./assets/icon-twitter.svg" alt="twitter" /></li>
        </ul>
      </footer>
    </div>
  </div>
</template>
<script>
import AddCard from "./components/AddCard.vue";
import QA from "./components/QA.vue";
export default {
  data() {
    return {
      features: {
        current: 0,
        tabs: [
          {
            navigator: "Simple Bookmarking",
            title: "Bookmark in one click",
            description:
              "Organize your bookmarks however you like. Our simple drag-and-drop interface gives you complete control over how you manage yourfavourite sites.",
          },
          {
            navigator: "Speedy Searching",
            title: "Intelligent search",
            description:
              "Our powerful search feature will help you find saved sites in no time at all. No need to trawl through all of your bookmarks.",
          },
          {
            navigator: "Easy Sharing",
            title: "Share your bookmarks ",
            description:
              "Easily share your bookmarks and collections with others. Create a shareable link that you can send at the click of a button.",
          },
        ],
      },
      browsers: [
        { name: "Chrome", version: 62 },
        { name: "Firefox", version: 55 },
        { name: "Opera", version: 64 },
      ],
      QA: [
        {
          question: "What is Bookmark?",
          answer:
            "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Fusce tincidunt justo eget ultricies fringilla. Phasellus blandit ipsum quisquam ornare mattis.",
          state: false,
        },
        {
          question: "How can I request a new browser?",
          answer:
            "Vivamus luctus eros aliquet convallis ultricies. Mauris augue massa, ultricies non ligula. Suspendisse imperdiet. Vivamus luctus erosaliquet convallis ultricies. Mauris augue massa, ultricies non ligula. Suspendisse imperdie tVivamus luctus eros aliquet convallis ultricies.Mauris augue massa, ultricies non ligula. Suspendisse imperdiet.",
          state: false,
        },
        {
          question: "Is there a mobile app?",
          answer:
            "Sed consectetur quam id neque fermentum accumsan. Praesent luctus vestibulum dolor, ut condimentum urna vulputate eget. Cras in ligula quis est pharetra mattis sit amet pharetra purus. Sed sollicitudin ex et ultricies bibendum.",
          state: false,
        },
        {
          question: "What about other Chromium browsers?",
          answer:
            "Integer condimentum ipsum id imperdiet finibus. Vivamus in placerat mi, at euismod dui. Aliquam vitae neque eget nisl gravida pellentesquenon ut velit.",
          state: false,
        },
      ],
    };
  },
  methods: {
    showAnswer(i) {
      if (i.state) {
        i.state = false;
      } else {
        this.QA.forEach((item) => (item.state = false));
        i.state = true;
      }
    },
  },
  components: { AddCard, QA },
};
</script>

<style>
.title {
  @apply text-dark-blue font-semibold;
}
section,
nav,
footer {
  @apply lg:px-32;
}
ul {
  @apply flex;
}
.smooth,
button {
  @apply transition duration-300;
}
</style>
