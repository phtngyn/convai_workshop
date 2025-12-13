<script setup lang="ts">
import { ref } from 'vue'

const texts = [
  "ReAct improves accuracy and citation coverage.",
  "ReAct helps on complex questions, not simple lookups.",
  "Visible reasoning increases trust and satisfaction."
]

const selected = ref<string[]>([])

function select(text: string) {
  if (selected.value.includes(text)) {
    selected.value = selected.value.filter(s => s !== text)
  } else {
    selected.value.push(text)
  }
}
</script>

<template>
  <div class="grid grid-cols-3 gap-12 pt-10">
    <div v-for="text in texts" key="text" class="[grid-auto-rows:1fr]">
      <button
        class="relative size-full pt-8 px-4 rounded-2xl border-2 text-left transition-all duration-200 hover:scale-[1.02] active:scale-[0.98]"
        :class="selected.includes(text)
          ? 'border-white bg-white/10 shadow-lg shadow-white/20'
          : 'border-white/30 bg-transparent hover:border-white/50 hover:bg-white/5'" @click="select(text)">
        <p class="text-white text-lg leading-relaxed">{{ text }}</p>

        <div v-if="selected.includes(text)"
          class="absolute top-4 right-4 size-6 rounded-full bg-white flex items-center justify-center">
          <svg class="w-4 h-4 text-black" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path strokeLinecap="round" strokeLinejoin="round" strokeWidth={3} d="M5 13l4 4L19 7" />
          </svg>
        </div>
      </button>
    </div>
  </div>
</template>
