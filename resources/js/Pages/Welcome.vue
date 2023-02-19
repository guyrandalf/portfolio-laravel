<script setup>
import { Head, Link } from "@inertiajs/inertia-vue3";
import FrontendLayout from '@/Layouts/Frontend.vue';
import Promote from "@/Components/Frontend/Promote.vue";
import Hero from '@/Components/Frontend/Hero.vue';
import About from '@/Components/Frontend/About.vue';
import Skills from '@/Components/Frontend/Skills.vue';
import Portfolio from '@/Components/Frontend/Portfolio.vue';
import Services from '@/Components/Frontend/Services.vue';

defineProps({
    skills: Object,
    projects: Object,
});
</script>

<template>
    <Head title="Welcome to my portfolio" />
    <FrontendLayout>
        <Hero />
        <Promote />
        <About />
        <Skills :skills="skills" />        
        <Portfolio :skills="skills" :projects="projects" />
        <Services />
    </FrontendLayout>
</template>