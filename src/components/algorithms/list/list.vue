<template>
  <div>

    <br>
    <h1>
      <pre class="grid place-content-center -mt-18 max-md:-mt-0 text-xl max-md:text-[8px] max-md:leading-[10px]">
██╗     ██╗███████╗████████╗
██║     ██║██╔════╝╚══██╔══╝
██║     ██║███████╗   ██║
██║     ██║╚════██║   ██║
███████╗██║███████║   ██║
╚══════╝╚═╝╚══════╝   ╚═╝
      </pre>
    </h1>

    <div class="text-orange-dark dark:text-purple-light mx-10 max-md:mx-6 my-5 text-xl max-md:text-base text-justify">
      <span class="defineList" />

      <br> <br>

      <div id="showList" class="hidden">

        <div class="grid grid-cols-2 gap-4 max-md:gap-2 place-content-stretch justify-items-center
                    max-md:flex max-md:flex-col text-center">
          <RouterLink :to="`list/${algorithm}`" v-for="algorithm in algorithms"
            class="w-full rounded-lg max-md:text-sm p-4 max-md:p-2 bg-orange-light text-orange-dark dark:bg-purple-light dark:text-vampire-dark
                    hover:animate-pulse">
              <p class="capitalize">
                {{ algorithm }}
              </p>
          </RouterLink >
        </div>

      </div>

    </div>

  </div>
</template>

<script>
  import { RouterLink } from 'vue-router'
  import item from '@/utils/cursor-item.js';
  import Typed from 'typed.js';

  export default {
    data () {
      return {
        algorithms: [
          'direct-route',
          'invert-route',
        ]
      }
    },
    mounted () {
      const listDefinition = [this.defList.list]

      new Typed('.defineList', {
        strings: listDefinition,
        typeSpeed: 25,
        cursorChar: item,
        loop: false,

        onComplete: () => {
          let show = document.getElementById('showList')
          show.classList.remove('hidden')
        }
      })
    },
    computed: {
      defList () {
        return this.$tm('components.index.list')
      }
    }
  }

</script>
