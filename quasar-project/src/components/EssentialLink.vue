<template>
  <q-item @click="navigate">
    <q-item-section avatar>
      <q-icon :name="icon" />
    </q-item-section>
    <q-item-section>
      <q-item-label>{{ title }}</q-item-label>
      <q-item-label caption>{{ caption }}</q-item-label>
    </q-item-section>
  </q-item>
</template>

<script setup>
import { defineProps } from 'vue'
import { useRouter } from 'vue-router'

const props = defineProps(['title', 'caption', 'icon', 'link'])
const router = useRouter()

function navigate() {
  router.push(link)
}
</script>

<style scoped>
/* Stilovi za EssentialLink */
</style>