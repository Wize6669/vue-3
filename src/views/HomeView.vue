<script setup>
import Hero from "@/components/Hero.vue";
import HomeCards from "@/components/HomeCards.vue";
import JobListings from "@/components/JobListings.vue";
import JSON from "@/components/JSON.vue";
</script>

<template>
  <Hero title="Become a Vue Dev" subtitle="Find the Vue job that fits your skills and needs"/>
  <HomeCards/>
  <JobListings :limit="10" :showButton="true"/>

  <hr/>

  <JSON/>
</template>
