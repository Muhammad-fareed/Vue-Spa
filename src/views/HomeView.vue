<script setup>
import Hero from '@/components/Hero.vue'
import HomeCards from '@/components/HomeCards.vue'
import JobListnings from '@/components/JobListnings.vue'
</script>
<template>
  <Hero />
  <HomeCards />
  <JobListnings :limit="2" :show-button="true"/>
</template>