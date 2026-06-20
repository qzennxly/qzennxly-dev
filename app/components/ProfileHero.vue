<template>
  <section class="space-y-8 pt-12 animate-[fadeIn_1s_ease-out_both] flex flex-col md:flex-row md:items-center gap-8 md:gap-12">
    <!-- Mavi Parıltılı & Dönüş Efektli Profil Resmi -->
    <div class="relative group mx-auto md:mx-0 flex-shrink-0">
      <div class="absolute -inset-4 rounded-full border border-dashed border-blue-500/20 animate-[spin_30s_linear_infinite] pointer-events-none"></div>
      <div class="absolute -inset-1.5 bg-gradient-to-r from-blue-600 to-cyan-400 rounded-full blur-md opacity-25 group-hover:opacity-60 transition duration-1000"></div>
      
      <img 
        src="https://github.com/qzennxly.png" 
        alt="qzennxly" 
        class="relative w-28 h-28 rounded-full border border-blue-900 bg-[#02040a] object-cover transition-transform duration-500 group-hover:scale-105"
      />
      <span class="absolute bottom-1 right-2 w-4 h-4 bg-cyan-400 border-2 border-black rounded-full animate-pulse"></span>
    </div>

    <!-- Başlık ve Tanımlar -->
    <div class="space-y-4 text-center md:text-left">
      <div class="inline-flex items-center gap-2 bg-blue-950/20 border border-blue-900/40 rounded-full px-3.5 py-1">
        <span class="w-1.5 h-1.5 rounded-full bg-cyan-400 animate-pulse"></span>
        <span class="font-mono text-[9px] tracking-widest text-blue-300">Full-Stack Developer</span>
      </div>
      
      <div class="space-y-2">
        <h1 class="text-4xl md:text-5xl font-black tracking-tight text-white leading-none">
          qzennxly<span class="text-transparent bg-clip-text bg-gradient-to-r from-blue-500 to-cyan-400">.dev</span>
        </h1>
        <p class="text-neutral-400 text-xs md:text-sm font-sans max-w-xl leading-relaxed">
          Merhaba Ben Kerem, 16 Yaşındayım. Nuxt 4 ve Tailwind CSS ile Web Siteleri Geliştiriyorum. Günümün Çoğunu Arayüz Tasarımı ve Kod Yazarak Geçiriyorum.
        </p>
      </div>

      <div class="flex justify-center md:justify-start gap-4 pt-1 font-mono text-[10px]">
        <a 
          href="https://github.com/qzennxly" 
          target="_blank" 
          class="text-blue-400 hover:text-cyan-400 transition-colors underline underline-offset-4"
        >
          GITHUB PROFİLİ
        </a>
        <span class="text-neutral-800">/</span>
        <a 
          href="mailto:contact@qzennxly.dev" 
          class="text-blue-400 hover:text-cyan-400 transition-colors underline underline-offset-4"
        >
          İLETİŞİME GEÇ
        </a>
      </div>
    </div>
  </section>
</template>

<style>
@keyframes fadeIn {
  from { opacity: 0; transform: translateY(20px); }
  to { opacity: 1; transform: translateY(0); }
}
</style>