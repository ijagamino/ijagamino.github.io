<template>
  <UPageSection
    :title="page.skills.title"
    :ui="{
      container: 'p-0!',
      title: 'text-left text-xl sm:text-xl lg:text-2xl font-medium',
      body: 'mt-2 grid grid-cols-2 lg:grid-cols-5 gap-4'
    }"
  >
    <template #body>
      <UCard
        v-for="(item, index) in page.skills.items"
        :key="index"
        :ui="{
          body: 'relative text-center',
          footer: 'text-sm font-medium text-center'
        }"
      >
        <div
          v-if="item.extras?.length !== undefined && item.extras?.length > 0"
          class="absolute flex gap-1 left-4 bottom-2"
        >
          <span
            v-for="extra in item.extras"
            :key="extra.icon"
          >
            <UIcon
              class="size-6 bg-neutral"
              :name="extra.icon"
            />
          </span>
        </div>
        <UIcon
          class="size-16 bg-primary"
          :name="item.icon"
        />
        <template #footer>
          {{
            item.extras !== undefined && item.extras.length > 0
              ? `${item.name} (${item.extras.map(extra => extra.name).join(', ')})`
              : item.name
          }}
        </template>
      </UCard>
    </template>
  </UPageSection>
</template>

<script setup lang="ts">
import type { IndexCollectionItem } from '@nuxt/content'

defineProps<{
  page: IndexCollectionItem
}>()
</script>
