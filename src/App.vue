<script setup lang="ts">
import { useHead } from '@vueuse/head'
import { isDark, preferredDark } from '~/composables/dark'

useHead({
  title: 'Stater Vue Lite',
  meta: [
    { name: 'description', content: 'Opinionated Vue Starter Template' },
    {
      name: 'theme-color',
      content: computed(() => isDark.value ? '#00aba9' : '#ffffff'),
    },
  ],
  link: [
    {
      rel: 'icon',
      type: 'image/svg+xml',
      href: computed(() => preferredDark.value ? '/favicon-dark.svg' : '/favicon.svg'),
    },
  ],
})
</script>

<template>
  <RouterView />
</template>
