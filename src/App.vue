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
          <RouterLink to="/accordeon" class="text-red-500 underline" active-class="text-blue-600 underline"> Accordéon
          </RouterLink>
          <RouterLink to="/boucles" class="text-red-500 underline" active-class="text-blue-600 underline">Boucles
          </RouterLink>
        </li>
      </ul>
    </nav>
  </header>
  <button @pointerdown="menuIsOpen = !menuIsOpen" aria-controls="mainNav" aria-expanded="true"
    class="rounded-sm border-2 border-teal-600 bg-teal-200 px-4 py-2 m-2">
    menu
  </button>
  <!-- nav#mainNav>ul>li*3>a[href="#"]{item $} -->
  <Transition class="transition-transform duration-1000" enter-from-class="-translate-x-full"
    enter-to-class="translate-x-0" leave-active-class="-translate-x-full">
    <nav id="mainNav" v-show="menuIsOpen" class="bg-gray-700 w-1/6 text-teal-100 flex justify-center py-4">
      <ul class="flex-col justify-center">
        <li class="py-3 hover:text-indigo-100 active:text-indigo-100">
          <RouterLink to="/"> Accueil </RouterLink>
        </li>
        <li class="py-3 hover:text-indigo-100 active:text-indigo-100">
          <RouterLink to="/accordeon"> Accordéon
          </RouterLink>
        </li>
        <li class="py-3 hover:text-indigo-100 active:text-indigo-100">
          <RouterLink to="/boucles">Boucles
          </RouterLink>
        </li>
      </ul>
    </nav>
  </Transition>
  <RouterView v-slot="{ Component }">
    <Suspense>
      <component :is="Component" />
    </Suspense>
  </RouterView>
</template>
