<script setup>
import { defineProps } from 'vue';
import { ref } from 'vue';
import jobData from '@/jobs.json';
const jobs = ref(jobData);

console.log(jobs.value);
</script>

<template>
    <section class="bg-blue-50 px-4 py-10">
        <div class = "container-xl lg:container m-auto">
            <h2 class = "text-3xl font-bold text-green-500 mb-6 text-center">
                
            </h2>
        </div>
        <div v-for="job in jobs" :key = "job.id">
            <h2>{{ job.title }}</h2>
            <p>{{ job.company }}</p>
            <p>{{ job.location }}</p>
            <p>{{ job.type }}</p>
            <p>{{ job.description }}</p>
            
        </div>
    </section>
</template>