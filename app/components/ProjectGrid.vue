<template>
  <div ref="projectRef" class="space-y-8">
    <div>
      <span class="font-mono text-[9px] text-blue-500 uppercase tracking-widest">03 / PROJELER</span>
      <h2 class="text-base font-bold text-white font-mono mt-1">SEÇİLMİŞ ÇALIŞMALAR</h2>
    </div>

    <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
      <a 
        v-for="(project, index) in projects" 
        :key="project.title"
        :href="project.link"
        target="_blank"
        class="p-6 rounded-lg border border-blue-950/60 bg-[#02040a]/30 backdrop-blur-md flex flex-col justify-between group transition-all duration-500 hover:border-blue-500/70 hover:shadow-[0_0_30px_rgba(0,102,255,0.08)] transform relative overflow-hidden"
        :class="isVisible ? 'translate-y-0 opacity-100' : 'translate-y-8 opacity-0'"
        :style="{ transitionDelay: `${index * 150}ms` }"
      >
        <!-- Lazer Tarama (Scanline) Çizgisi -->
        <div class="absolute left-0 right-0 h-[2px] bg-gradient-to-r from-transparent via-cyan-400 to-transparent opacity-0 group-hover:opacity-100 group-hover:animate-scan pointer-events-none"></div>

        <div class="space-y-4 relative z-10">
          <div class="flex justify-between items-start">
            <h3 class="font-mono text-xs font-bold text-neutral-200 group-hover:text-blue-400 transition-colors">
              {{ project.title }}
            </h3>
            <span class="text-blue-900 group-hover:text-blue-400 transition-colors duration-300">
              <svg xmlns="http://www.w3.org/2000/svg" width="13" height="13" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><path d="M15 3h6v6"/><path d="M10 14 21 3"/><path d="M18 13v6a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V8a2 2 0 0 1 2-2h6"/></svg>
            </span>
          </div>
          <p class="text-neutral-400 text-[11px] leading-relaxed">
            {{ project.desc }}
          </p>
        </div>

        <div class="mt-6 flex flex-wrap gap-1.5 relative z-10">
          <span 
            v-for="tag in project.tags" 
            :key="tag"
            class="text-[9px] font-mono bg-[#050814] border border-blue-950/60 text-blue-400 px-2 py-0.5 rounded"
          >
            #{{ tag }}
          </span>
        </div>
      </a>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const projectRef = ref(null)
const isVisible = ref(false)

const projects = [
  {
    title: 'qzennxly Portfolio',
    desc: 'Nuxt 4 mimarisi ve Tailwind CSS kullanılarak saf siyah arka plan üzerine kurgulanan, imleç etkileşimli modern ön yüz portfolyo çalışması.',
    tags: ['Nuxt 4', 'PostgreSQL', 'TailwindCSS', 'Prisma'],
    link: 'https://github.com/qzennxly/qzennxly-dev'
  },
  {
    title: 'MangaDear',
    desc: 'Kullanıcıların en sevdikleri mangaları yüksek hız ve kesintisiz arayüz performansı ile okuyabilmesi için optimize edilmiş modern manga okuma platformu.',
    tags: ['Nuxt 4', 'PostgreSQL', 'TailwindCSS', 'Prisma'],
    link: 'https://github.com/qzennxly/mangadear'
  }
]

onMounted(() => {
  const observer = new IntersectionObserver(([entry]) => {
    if (entry.isIntersecting) {
      isVisible.value = true
      observer.disconnect()
    }
  }, { threshold: 0.15 })

  if (projectRef.value) observer.observe(projectRef.value)
})
</script>

<style scoped>
@keyframes scan {
  0% { top: -10%; opacity: 0; }
  10% { opacity: 1; }
  90% { opacity: 1; }
  100% { top: 110%; opacity: 0; }
}
.group-hover\:animate-scan {
  animation: scan 2s cubic-bezier(0.4, 0, 0.2, 1) infinite;
}
</style>