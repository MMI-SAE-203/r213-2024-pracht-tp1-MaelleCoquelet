<script setup lang="ts">
//
import { ref } from 'vue'
const sectionOpen = ref(1)
</script>

<template>
  <p>bonjour</p>
  <section>
    <button class="text-xl" @pointerdown="sectionOpen = sectionOpen === 1 ? 0 : 1">bouton 1</button>
    <p v-show="sectionOpen === 1">
      Lorem ipsum dolor sit amet consectetur adipisicing elit. Hic aut temporibus quae delectus
      aliquam alias molestias minima. Itaque, magni corrupti eos quos neque praesentium animi
      dolorem fugit ullam, excepturi aperiam.
    </p>
  </section>
  <section>
    <button class="text-xl" @pointerdown="sectionOpen = sectionOpen === 2 ? 0 : 2">bouton 2</button>
    <p v-show="sectionOpen === 2">
      Magnam adipisci sequi quas architecto. Impedit id ut illum maxime necessitatibus! Incidunt,
      cupiditate. Molestiae culpa id ratione expedita placeat officiis asperiores quam quasi
      doloremque aut. Consectetur aperiam iure numquam laboriosam.
    </p>
  </section>
  <section>
    <button class="text-xl" @pointerdown="sectionOpen = sectionOpen === 3 ? 0 : 3">bouton 3</button>
    <p v-show="sectionOpen === 3">
      Alias corporis vero aut placeat iste amet dolores reprehenderit provident tempora! Porro, cum.
      Neque laborum accusamus et ut perspiciatis repudiandae aliquam pariatur, ea molestias eligendi
      esse veritatis, asperiores cupiditate enim.
    </p>
  </section>
</template>