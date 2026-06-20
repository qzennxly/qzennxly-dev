<template>
  <div ref="matrixRef" class="space-y-8">
    <div>
      <span class="font-mono text-[9px] text-blue-500 uppercase tracking-widest">01 / YETKİNLİK SİSTEMİ</span>
      <h2 class="text-base font-bold text-white font-mono mt-1">TEKNOLOJİK MATRİS</h2>
    </div>

    <!-- Teknolojiler Grid'i -->
    <div class="grid grid-cols-2 sm:grid-cols-3 md:grid-cols-5 gap-3">
      <div 
        v-for="(tech, index) in skills" 
        :key="tech.name"
        class="p-4 rounded-lg border border-blue-950/60 bg-[#02040a]/40 backdrop-blur-md flex flex-col items-center justify-center gap-3 transition-all duration-500 hover:border-blue-500/70 hover:shadow-[0_0_20px_rgba(0,102,255,0.12)] group transform"
        :class="isVisible ? 'translate-y-0 opacity-100' : 'translate-y-12 opacity-0'"
        :style="{ transitionDelay: `${index * 80}ms` }"
      >
        <!-- 3D Dönen İkon Konteyneri -->
        <div class="w-10 h-10 flex items-center justify-center relative transition-transform duration-700 ease-out group-hover:[transform:rotateY(360deg)]">
          <img 
            :src="tech.icon" 
            :alt="tech.name"
            class="w-8 h-8 object-contain filter drop-shadow-[0_0_8px_rgba(0,210,255,0.4)]"
          />
        </div>
        
        <span class="font-mono text-[9px] text-neutral-400 group-hover:text-blue-300 transition-colors">
          {{ tech.name }}
        </span>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const matrixRef = ref(null)
const isVisible = ref(false)

// SimpleIcons CDN üzerinden Mavi/Siyan renkli dinamik SVG'ler
const skills = [
  { name: 'HTML5', icon: 'https://cdn.simpleicons.org/html5/00d2ff' },
  { name: 'CSS3', icon: 'https://cdn.simpleicons.org/css/00d2ff' },
  { name: 'JavaScript', icon: 'https://cdn.simpleicons.org/javascript/00d2ff' },
  { name: 'TailwindCSS', icon: 'https://cdn.simpleicons.org/tailwindcss/00d2ff' },
  { name: 'Vue.js', icon: 'https://cdn.simpleicons.org/vuedotjs/00d2ff' },
  { name: 'Nuxt', icon: 'https://cdn.simpleicons.org/nuxt/00d2ff' },
  { name: 'React', icon: 'https://cdn.simpleicons.org/react/00d2ff' },
  { name: 'Next.js', icon: 'https://cdn.simpleicons.org/nextdotjs/00d2ff' },
  { name: 'PostgreSQL', icon: 'https://cdn.simpleicons.org/postgresql/00d2ff' },
  { name: 'Prisma', icon: 'https://cdn.simpleicons.org/prisma/00d2ff' }
]

onMounted(() => {
  const observer = new IntersectionObserver(([entry]) => {
    if (entry.isIntersecting) {
      isVisible.value = true
      observer.disconnect()
    }
  }, { threshold: 0.12 })

  if (matrixRef.value) observer.observe(matrixRef.value)
})
</script>