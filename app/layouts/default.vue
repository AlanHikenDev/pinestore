<script setup lang="ts">
  /* Vuetify useTheme will not work with SSR enabled, more info - https://nuxt.vuetifyjs.com/guide/server-side-rendering.html#vuetify-themes */
  // import { useCustomTheme } from '~/composables/custom-theme'
  // const { isDark } = useCustomTheme()

  /* Update on using the above technique - We now use SSR HTTP Client hints technique instead of the above - https://nuxt.vuetifyjs.com/guide/server-side-rendering.html#ssr-http-client-hints */

  const route = useRoute()

  const pageMeta = computed(() => {
    return {
      title: route.meta.title,
      description: route.meta.description,
      ogImage: route.meta.ogImage,
      canonicalUrl: route.meta.canonicalUrl || route.fullPath,
      generator: route.meta.generator,
      tags: route.meta.tags,
    }
  })

  useHeadAndMeta(pageMeta)
  useOgImage()
</script>

<template>
  <div>
    <!-- <div class="container mx-auto"> -->
    <v-app
      class="min-h-screen bg-white dark:bg-neutral-950 text-neutral-900 dark:text-neutral-50"
    >
      <!-- <v-app :theme="isDark ? 'dark' : 'light'"> -->
      <!-- https://vuetifyjs.com/en/features/application-layout/
        Navbar contains all nav components such as v-app-bar, v-system-bar, v-navigation-drawer, v-bottom-navigation -->
      <NavBar />
      <v-main class="py-4">
        <slot />
      </v-main>
      <!-- https://vuetifyjs.com/en/features/application-layout/
        TheFooter contains the v-footer -->
      <TheFooter />
    </v-app>
    <!-- </div> -->
  </div>
</template>
<style></style>
