<script setup lang="ts">
import { onErrorCaptured } from 'vue'
import { ref } from 'vue'
import { RouterLink, RouterView } from 'vue-router/auto'

onErrorCaptured((err, instance, info) => {
  console.error('erreur : ', err, '\ninfo : ', info, '\ncomposant : ', instance)
  return true
})
const menuIsOpen = ref(false)
</script>

<template>
  <header>
    <nav>
      <ul>
        <li>
          <RouterLink to="/" class="text-red-500 underline"> Accueil </RouterLink>
          <RouterLink to="/accordeon" class="text-red-500 underline" active-class="text-blue-600 underline"> Accordéon </RouterLink>
          <RouterLink to="/boucles" class="text-red-500 underline" active-class="text-blue-600 underline">Boucles</RouterLink>
        </li>
      </ul>
    </nav>
  </header>
  <button
    @pointerdown="menuIsOpen = !menuIsOpen"
    aria-controls="mainNav"
    aria-expanded="true"
    class="rounded-full border-2 border-red-600 bg-red-300 px-2"
  >
    menu
  </button>
  <!-- nav#mainNav>ul>li*3>a[href="#"]{item $} -->
  <Transition
    class="transition-transform duration-700"
    enter-from-class="-translate-x-full"
    enter-to-class="translate-x-0"
    leave-active-class="-translate-x-full"
  >
    <nav id="mainNav" v-show="menuIsOpen">
      <ul>
        <li><a href="#">item 1</a></li>
        <li><a href="#">item 2</a></li>
        <li><a href="#">item 3</a></li>
      </ul>
    </nav>
  </Transition>
  <RouterView v-slot="{ Component }">
    <Suspense>
      <component :is="Component" />
    </Suspense>
  </RouterView>
</template>
