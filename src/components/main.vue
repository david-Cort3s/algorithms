<template>
  <div class="h-full mr-2">
    <div class="h-full flex flex-col justify-between">
      <nav class="flex flex-col h-3/6">
        <div class="h-full m-40 max-md:m-10 max-md:p-0 p-10">
          <div class="bg-logo-light dark:bg-logo-dark mx-auto w-40 h-40 bg-center bg-no-repeat">
            &nbsp
          </div>
          <p class="text-4xl text-center">
            {{ main.title }}
          </p>
          <p class="text-md max-md:text-lg text-center mb-32 animate-pulse text-orange-dark dark:text-purple-light">
            {{ main.version }}
          </p>
        </div>
      </nav>

      <main>
        <div class="columns-5 max-md:flex max-md:flex-col">
          <div v-for="(folder, key) in main.folders" class="max-md:py-1 py-2 grid place-items-center">
            <RouterLink :to="`${key}`" class="w-full max-md:p-2 py-6 rounded-lg text-center bg-orange-light text-orange-dark dark:bg-purple-light dark:text-purple-dark">
              <p class="capitalize">
                {{ folder }}
              </p>
            </RouterLink>
          </div>
        </div>
      </main>
    </div>
  </div>
</template>

<script>
  import { RouterLink } from 'vue-router';

  export default {
    data () {
      return {
        folders: [
          'encrypt',
          'graph',
          'list',
          'math',
          'no',
          'search',
          'set',
          'sort',
          'string',
          'tree'
        ],
      }
    },
    computed: {
      main () {
        return this.$tm('components.main')
      }
    }
  }

</script>
