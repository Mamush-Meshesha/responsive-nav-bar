<script setup>
import { Icon } from "@iconify/vue";
import { computed, ref } from "vue";
import Button from "./components/Button.vue";
const links = [
  { name: "Home", link: "#" },
  { name: "Services", link: "#" },
  { name: "About", link: "#" },
  { name: "Blogs", link: "#" },
  { name: "Contact", link: "#" },
];

const open = ref(false);

const getIconName = computed(() => {
  return open.value
    ? "line-md:menu-to-close-transition"
    : "system-uicons:menu-hamburger";
});

const opneMenu = () => {
  return (open.value = !open.value);
};
</script>

<template>
  <div
    class="py-3 px-6 bg-black text-white md:flex justify-between items-center"
  >
    <div class="flex items-center">
      <span
        ><Icon icon="fe:messanger" class="text-green-500 text-5xl mr-1"
      /></span>
      <h1>Designer</h1>
    </div>
    <span
      @click="opneMenu"
      class="absolute md:hidden right-6 top-2 cursor-pointer"
    >
      <Icon :icon="getIconName" class="text-4xl text-white" />
    </span>
    <ul
      class="md:flex md:items-center md:px-0 px-3 md:pb-0 pb-10 md:static absolute bg-gray-950 md:w-auto w-full top-14 duration-700 ease-in"
      :class="[open ? 'left-0' : 'left-[-100%]']"
    >
      <li class="md:mx-4 md:my-0 my-6" v-for="link in links" :key="link.name">
        <a :href="link.link" class="text-xl hover:text-green-400">{{
          link.name
        }}</a>
      </li>
      <Button>Get started</Button>
    </ul>
  </div>
</template>
