<template>
  <div ref="timelineRef" class="space-y-10">
    <div>
      <span class="font-mono text-[9px] text-blue-500 uppercase tracking-widest">02 / KRONOLOJİ</span>
      <h2 class="text-base font-bold text-white font-mono mt-1">DENEYİM VE GELİŞİM SÜRECİ</h2>
    </div>

    <div class="relative pl-6 border-l border-dashed border-blue-900/40 space-y-8">
      <div 
        v-for="(step, index) in steps" 
        :key="step.year"
        class="relative transition-all duration-1000 transform"
        :class="isVisible ? 'translate-y-0 opacity-100' : 'translate-y-8 opacity-0'"
        :style="{ transitionDelay: `${index * 150}ms` }"
      >
        <span class="absolute -left-[30px] top-1.5 w-2 h-2 rounded-full bg-cyan-400">
          <span class="absolute -inset-1.5 rounded-full bg-cyan-400/40 animate-ping"></span>
        </span>

        <div class="space-y-1.5">
          <div class="flex items-center gap-3 font-mono">
            <span class="text-xs text-blue-400 font-semibold">{{ step.year }}</span>
            <span class="text-[9px] bg-blue-950/40 border border-blue-900/40 text-blue-300 px-2 py-0.5 rounded-full uppercase tracking-wider">{{ step.tag }}</span>
          </div>
          <h3 class="text-xs font-bold text-white font-mono">{{ step.title }}</h3>
          <p class="text-[11px] text-neutral-400 leading-relaxed font-sans max-w-xl">
            {{ step.desc }}
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const timelineRef = ref(null)
const isVisible = ref(false)

const steps = [
  {
    year: '2026',
    tag: 'Mühendislik',
    title: 'Nuxt 4 Performans Optimizasyonları',
    desc: 'Nuxt 4 üzerinde kod bölme (code-splitting), sunucu taraflı derleme (SSR) ve dinamik rotaların render optimizasyon süreçlerini yürütüyorum.'
  },
  {
    year: '2026',
    tag: 'Geliştirme',
    title: 'Modüler Arayüz Bileşenleri',
    desc: 'TypeScript temellerinde, yüksek oranda modüler ve erişilebilir web arabirim tasarımları gerçekleştiriyorum.'
  }
]

onMounted(() => {
  const observer = new IntersectionObserver(([entry]) => {
    if (entry.isIntersecting) {
      isVisible.value = true
      observer.disconnect()
    }
  }, { threshold: 0.15 })

  if (timelineRef.value) observer.observe(timelineRef.value)
})
</script>