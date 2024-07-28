<script lang="ts">
import HelloWorld from "@/components/HelloWorld.vue";
import TheWelcome from "@/components/TheWelcome.vue";
import JobsList from '@/components/JobsList.vue';
import { defineComponent, reactive, ref, toRefs } from "vue";
import { Job } from "./types/job";

export default defineComponent({
  name: "App",
  components: {JobsList, TheWelcome, HelloWorld },
  setup() {
    // ex 1 : use reactive
    // const state = reactive({
    //   name: 'Link',
    //   age: 20 as string | number
    // });
    // state.name = 'Link2';
    // state.age = 24;
    // return { ...toRefs(state) };

    // ex 2
    // const name = ref('link');
    // // const age = ref(20) as number | string; <- error
    // const age = ref<number|string>(25); // <- correct
    // return { name, age };

    const jobs = ref<Job[]>([
      {
        title: "farm worker",
        location: "lon lon ranch",
        salary: 30000,
        id: "1",
      },
      {
        title: "quarry man",
        location: "death mountain",
        salary: 40000,
        id: "2",
      },
      {
        title: "flute player",
        location: "the lost woods",
        salary: 35000,
        id: "3",
      },
      { title: "fisher man", location: "lake hylia", salary: 21000, id: "4" },
      {
        title: "prison guard",
        location: "gerudo valley",
        salary: 32000,
        id: "5",
      },
    ]);

    return { jobs };
  },
  methods: {
    //
  },
});
</script>

<template>
  <header>
    <img
      alt="Vue logo"
      class="logo"
      src="./assets/logo.svg"
      width="125"
      height="125"
    />

    <div class="wrapper">
      <HelloWorld msg="You did it!" />
    </div>
  </header>

  <main>
    <JobsList :jobs="jobs" />
    <TheWelcome />
  </main>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
