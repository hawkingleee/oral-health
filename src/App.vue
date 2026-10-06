<script setup>
import NavBar from './components/NavBar.vue'
import HeroSection from './components/HeroSection.vue'
import KnowledgeSection from './components/KnowledgeSection.vue'
import RoutineSection from './components/RoutineSection.vue'
import ToolsSection from './components/ToolsSection.vue'
import PlanSection from './components/PlanSection.vue'
import FaqSection from './components/FaqSection.vue'
import FooterBar from './components/FooterBar.vue'
</script>

<template>
  <NavBar />
  <main>
    <HeroSection />
    <KnowledgeSection />
    <RoutineSection />
    <ToolsSection />
    <PlanSection />
    <FaqSection />
  </main>
  <FooterBar />
</template>
