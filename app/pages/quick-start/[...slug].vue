<script setup lang="ts">
  import siteMeta from '@/site'
  const { github } = siteMeta

  definePageMeta({
    // layout: 'default',
    name: 'quick-start',
    // alias: '[...slug]',
    title: 'Quick Start',
    description: 'Start Strong, Start Fast: Your Quick Launch Guide!',
    navOrder: '4',
    type: 'primary',
    icon: 'i-mdi-home',
    // ogImage: 'images/ogImage.png', // url or local images inside public folder, for eg, ~/public/images/ogImage.png
  })

  const slug =
    useRoute().params.slug.toString().replace(/,/g, '/') ||
    useRoute().name.toString().replace(/,/g, '/')

  useServerSeoMeta({
    description: () => slug || '',
  })
</script>
<template>
  <div>
    <TheHeader>
      <div>
        <div class="flex items-center">
          <h2 class="text-5xl font-semibold">Quick Start</h2>
        </div>
        <div class="flex items-center mt-4">
          <h6>Github repo for this template</h6>
          <v-btn
            size="small"
            class="ml-2"
            color="secondary"
            :href="github"
            target="_blank"
          >
            <span class="text-sm text-subtitle-2">Click here</span>
          </v-btn>
        </div>
        <slot />
      </div>
    </TheHeader>
    <section class="container mx-auto">
      <div class="px-10 w-full">
        <div class="flex flex-col rounded-lg">
          <article
            class="dark:xl:divide-gray-700 xl:divide-gray-200 xl:divide-y"
          >
            <div
              class="dark:divide-gray-700 divide-gray-200 divide-y pb-16 xl:divide-y-0 xl:gap-x-10 xl:grid xl:grid-cols-4 xl:pb-20 xl:sticky"
              style="grid-template-rows: auto 1fr"
            >
              <div
                class="dark:divide-gray-700 divide-gray-200 divide-y xl:col-span-3 xl:pb-0 xl:row-span-2"
              >
                <StaticMarkdown :path="slug" />
              </div>
            </div>
          </article>
        </div>
      </div>
    </section>
  </div>
</template>
<style scoped></style>
