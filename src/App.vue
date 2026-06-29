<script setup>
import { onMounted } from 'vue'
import AppHeader from './components/AppHeader.vue'
import HeroSection from './components/HeroSection.vue'
import FeaturesSection from './components/FeaturesSection.vue'
import HowItWorksSection from './components/HowItWorksSection.vue'
import PricingSection from './components/PricingSection.vue'
import FaqSection from './components/FaqSection.vue'
import ContactSection from './components/ContactSection.vue'
import AppFooter from './components/AppFooter.vue'

// セクションがビューポートに入ったらフェードインさせる
// （演出はヒーローのスタンプに集約しているので、ここは控えめに）
onMounted(() => {
  const els = document.querySelectorAll('.reveal')
  const observer = new IntersectionObserver((entries) => {
    entries.forEach((entry) => {
      if (entry.isIntersecting) {
        entry.target.classList.add('in')
        observer.unobserve(entry.target)
      }
    })
  }, { threshold: 0.15 })
  els.forEach((el) => observer.observe(el))
})
</script>

<template>
  <AppHeader />
  <main id="top">
    <HeroSection />
    <hr class="perforation wrap" />
    <FeaturesSection />
    <HowItWorksSection />
    <PricingSection />
    <FaqSection />
    <ContactSection />
  </main>
  <AppFooter />
</template>
