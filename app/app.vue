<template>
  <div class="min-h-screen bg-[#000000] text-neutral-200 selection:bg-blue-600 selection:text-white font-sans antialiased relative overflow-x-hidden">
    
    <!-- İmleç Etkileşimli Mavi Enerji Tozları Tuvali -->
    <canvas 
      ref="energyCanvas" 
      class="fixed inset-0 pointer-events-none z-10 opacity-40"
    ></canvas>

    <div class="relative z-20">
      <NuxtPage />
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, onBeforeUnmount } from 'vue'

const energyCanvas = ref(null)
let animationFrameId = null
let handleResize = null

const mouseX = ref(-1000)
const mouseY = ref(-1000)

const updateMouse = (e) => {
  mouseX.value = e.clientX
  mouseY.value = e.clientY
}

onMounted(() => {
  const canvas = energyCanvas.value
  if (!canvas) return
  
  const ctx = canvas.getContext('2d')
  let width = window.innerWidth
  let height = window.innerHeight
  
  canvas.width = width
  canvas.height = height

  const numParticles = 90
  const particles = []

  for (let i = 0; i < numParticles; i++) {
    particles.push({
      x: Math.random() * width,
      y: Math.random() * height,
      baseX: Math.random() * width,
      baseY: Math.random() * height,
      r: Math.random() * 1.4 + 0.4,       // İnce enerji tanecikleri
      opacity: Math.random() * 0.5 + 0.15,
      vy: Math.random() * 0.4 + 0.1,      // Süzülme hızı
      vx: Math.random() * 0.2 - 0.1
    })
  }

  const animate = () => {
    ctx.clearRect(0, 0, width, height)
    
    for (let i = 0; i < numParticles; i++) {
      const p = particles[i]
      
      // Fizik motoru: İmleç yakınlığı hesaplama
      const dx = p.x - mouseX.value
      const dy = p.y - mouseY.value
      const distance = Math.sqrt(dx * dx + dy * dy)
      
      // İmleç etrafındaki 120px'lik koruma alanı
      if (distance < 120) {
        const force = (120 - distance) / 120
        // Parçacıkları imlecin ters yönüne iten kuvvet
        p.x += (dx / distance) * force * 4
        p.y += (dy / distance) * force * 4
      }

      ctx.beginPath()
      ctx.fillStyle = `rgba(0, 210, 255, ${p.opacity})` // Elektrik Siyanı
      ctx.arc(p.x, p.y, p.r, 0, Math.PI * 2, true)
      ctx.fill()

      p.y += p.vy
      p.x += p.vx

      // Ekrandan çıkan tanecikleri sıfırla
      if (p.y > height) {
        p.y = -5
        p.x = Math.random() * width
      }
      if (p.x > width) p.x = 0
      else if (p.x < 0) p.x = width
    }
    
    animationFrameId = requestAnimationFrame(animate)
  }

  handleResize = () => {
    width = window.innerWidth
    height = window.innerHeight
    canvas.width = width
    canvas.height = height
  }

  window.addEventListener('resize', handleResize)
  window.addEventListener('mousemove', updateMouse)
  animate()
})

onBeforeUnmount(() => {
  if (animationFrameId) cancelAnimationFrame(animationFrameId)
  if (handleResize) {
    window.removeEventListener('resize', handleResize)
    window.removeEventListener('mousemove', updateMouse)
  }
})
</script>

<style>
::-webkit-scrollbar {
  width: 5px;
}
::-webkit-scrollbar-track {
  background: #000000;
}
::-webkit-scrollbar-thumb {
  background: #001122;
  border-radius: 99px;
  border: 1px solid #0055ff;
}
::-webkit-scrollbar-thumb:hover {
  background: #0055ff;
}

html {
  scroll-behavior: smooth;
  background-color: #000000;
}

body {
  margin: 0;
  padding: 0;
  background-color: #000000;
}
</style>