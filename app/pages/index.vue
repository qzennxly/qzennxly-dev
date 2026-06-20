<template>
  <div class="relative min-h-screen pb-32">
    <!-- Neon Mavi Parıltı Katmanı -->
    <GlowingBackground />

    <!-- Yüzen Kapsül Menü -->
    <Navbar />

    <!-- Ana Portfolyo Akışı -->
    <main class="max-w-3xl mx-auto px-6 pt-36 space-y-24 relative z-20">
      
      <!-- GİRİŞ -->
      <section id="about" class="pt-6">
        <ProfileHero />
      </section>

      <!-- YETKİNLİK SİSTEMİ (Mavi SimpleIcons Grid'i) -->
      <section id="skills" class="pt-6">
        <TechMatrix />
      </section>

      <!-- KARİYER KRONOLOJİSİ -->
      <section id="timeline" class="pt-6">
        <ExperienceTimeline />
      </section>

      <!-- PROJELER (qzennxly-dev & MangaDear) -->
      <section id="projects" class="pt-6">
        <ProjectGrid />
      </section>

      <!-- ALT BİLGİ (FOOTER) -->
      <footer class="border-t border-blue-950/40 pt-16 text-center">
        <p class="text-[9px] font-mono text-neutral-500 tracking-widest uppercase">
          © {{ new Date().getFullYear() }} qzennxly. Sürdürülebilir arayüz mühendisliği standartları.
        </p>
      </footer>

    </main>
  </div>
</template>

<script setup>
import { useHead } from '#imports'

useHead({
  title: 'qzennxly — Full-Stack Developer',
  meta: [
    { name: 'description', content: 'Full-Stack Developer.' }
  ]
})
</script>