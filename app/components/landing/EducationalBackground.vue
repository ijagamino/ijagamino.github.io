<template>
  <UPageSection
    :title="page.educationalBackground.title"
    :ui="{
      container: 'p-0! gap-4 sm:gap-4',
      title: 'text-left text-xl sm:text-xl lg:text-2xl font-medium',
      body: 'mt-2'
    }"
  >
    <template #body>
      <UTimeline
        :items="page.educationalBackground.items"
        orientation="vertical"
        reverse
        :default-value="2"
      >
        <template #title="{ item }">
          {{ item.degree }}
        </template>
        <template #description="{ item }">
          {{ item.institution }}
        </template>
      </UTimeline>
    </template>
  </UPageSection>
</template>

<script setup lang="ts">
import type { IndexCollectionItem } from '@nuxt/content'

defineProps<{
  page: IndexCollectionItem
}>()
</script>
