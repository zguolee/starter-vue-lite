<script setup lang="ts">
import { useUserStore } from '~/stores/user'

const { currentRoute, back } = useRouter()
const userStore = useUserStore()

const name = computed(() => {
  if (currentRoute.value.name === '//hi/[name]')
    return currentRoute.value.params.name
  return ''
})

userStore.setNewName(name.value)
</script>

<template>
  <div class="px-4 pt-10">
    <div class="i-tabler-run text-5xl" />

    <p>
      {{ `Hi, ${name}` }}
    </p>

    <p class="py-4">
      <em class="text-sm opacity-75">Demo of dynamic route</em>
    </p>

    <template v-if="userStore.otherNames.length">
      <p mt-4 text-sm>
        <span opacity-75>Also known as:</span>
        <ul>
          <li v-for="otherName in userStore.otherNames" :key="otherName">
            <RouterLink :to="`/hi/${otherName}`" replace>
              {{ otherName }}
            </RouterLink>
          </li>
        </ul>
      </p>
    </template>

    <div class="m-4">
      <button
        class="inline-block cursor-pointer rounded bg-blue-500 px-4 py-1 text-white hover:bg-blue-600"
        @click="back()"
      >
        Back
      </button>
    </div>
  </div>
</template>
