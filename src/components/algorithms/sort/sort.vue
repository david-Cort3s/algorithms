<template>
  <div>
    <br />
    <h1>
      <pre class="-mt-18 grid place-content-center text-xl max-md:-mt-0 max-md:text-[8px] max-md:leading-[10px]">
███████╗ ██████╗ ██████╗ ████████╗
██╔════╝██╔═══██╗██╔══██╗╚══██╔══╝
███████╗██║   ██║██████╔╝   ██║
╚════██║██║   ██║██╔══██╗   ██║
███████║╚██████╔╝██║  ██║   ██║
╚══════╝ ╚═════╝ ╚═╝  ╚═╝   ╚═╝
      </pre>
    </h1>

    <div class="mx-10 my-5 text-justify text-xl text-orange-dark max-md:mx-6 max-md:text-base dark:text-purple-light">
      <span class="defineSort" />

      <br />
      <br />

      <div
        id="showSort"
        class="hidden"
      >
        <div
          class="grid grid-cols-2 place-content-stretch justify-items-center gap-4 text-center max-md:flex max-md:flex-col max-md:gap-2"
        >
          <RouterLink
            :to="`sort/${algorithm}`"
            v-for="algorithm in algorithms"
            class="w-full rounded-lg bg-orange-light p-4 text-orange-dark hover:animate-pulse max-md:p-2 max-md:text-sm dark:bg-purple-light dark:text-vampire-dark"
          >
            <p class="capitalize">
              {{ algorithm }}
            </p>
          </RouterLink>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  import { RouterLink } from "vue-router";
  import item from "@/utils/cursor-item.js";
  import Typed from "typed.js";

  export default {
    data() {
      return {
        algorithms: [
          "accounts",
          "bubble",
          "heap",
          "insertion",
          "merge",
          "quicksort",
          "radix",
          "selection",
          "shellsort",
        ],
      };
    },
    computed: {
      defSort() {
        return this.$tm("components.index.sort");
      },
    },
    mounted() {
      const sortDefinition = [this.defSort.sort];

      new Typed(".defineSort", {
        strings: sortDefinition,
        typeSpeed: 25,
        cursorChar: item,
        loop: false,

        onComplete: () => {
          let show = document.getElementById("showSort");
          show.classList.remove("hidden");
        },
      });
    },
  };
</script>
