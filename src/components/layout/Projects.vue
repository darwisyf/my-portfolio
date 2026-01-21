<template>
    <section id="projects" class="relative w-11/12 px-16 mx-auto">
        <SectionHeader title="My Projects" />
        <!-- Custom Navigation Buttons -->
        <button
            class="swiper-prev absolute top-2/3 left-4 transform -translate-y-1/2 z-10 text-white dark:bg-secondary bg-primary p-4 rounded-full">
            <Icon icon="line-md:arrow-left-circle" class="font-bold text-3xl" />
        </button>
        <button
            class="swiper-next absolute top-2/3 right-4 transform -translate-y-1/2 z-10 text-white dark:bg-secondary bg-primary p-4 rounded-full">
            <Icon icon="line-md:arrow-right-circle" class="font-bold text-3xl" />
        </button>

        <!-- Swiper Components -->
        <swiper :effect="'coverflow'" grabCursor centeredSlides :slidesPerView="'auto'" :coverflowEffect="{
            rotate: 50,
            stretch: 0,
            depth: 100,
            modifier: 1,
            slideShadows: true,
        }" :navigation="navigationOptions" pagination :modules="[EffectCoverflow, Navigation]"
            class="max-w-full mt-32">
            <swiper-slide class="max-w-[300px]" v-for="(project, index) in projects" :key="index">
                <ProjectCard :title="project.title" :description="project.desc"
                    :image="'src/assets/images/' + project.image" :tags="project.tag" :liveLink="project.liveLink"
                    :codeLink="project.codeLink" />
            </swiper-slide>
        </swiper>
    </section>
</template>
<script setup>
import { ref } from 'vue';
import SectionHeader from '@/components/UI/SectionHeader.vue';
import ProjectCard from '@/components/UI/ProjectCard.vue';
import 'swiper/css';
import 'swiper/css/effect-coverflow';
import 'swiper/css/navigation';
import 'swiper/css/pagination';
import { Swiper, SwiperSlide } from 'swiper/vue';
import { EffectCoverflow, Navigation } from 'swiper/modules';
import { Icon } from '@iconify/vue';

// Define navigation options
const navigationOptions = {
    prevEl: '.swiper-prev',
    nextEl: '.swiper-next'
}

const projects = ref([
    {
        title: 'Portfolio Website',
        desc: 'A Website i made using VueJS and TailwindCSS and some CSS and JS library',
        image: '/Portfolio Website.png',
        tag: ['VueJS', 'TailwindCSS'],
        liveLink: '/',
        codeLink: "https://github.com/darwisyf/my-portfolio",
    },
    {
        title: 'Production Dashboard',
        desc: 'An internal data visualization i made using Power BI from Production Database at PT. TMMIN',
        image: '/Production Dashboard.png',
        tag: ['PowerBI', 'PostgreSQL', 'Sharepoint', 'PowerQuery'],
        liveLink: '',
        codeLink: "",
    },
    {
        title: 'Safety Dashboard',
        desc: 'An internal data visualization i made using Power BI from Safety Database at PT. TMMIN',
        image: '/Safety Dashboard.jpeg',
        tag: ['PowerBI', 'PostgreSQL', 'Sharepoint', 'PowerQuery'],
        liveLink: '',
        codeLink: "",
    },
    {
        title: 'Accounting Web Application (Unfinished)',
        desc: 'My personal project for learning Fullstack Web Development using Laravel 12 and Tailwindcss',
        image: '/Accounting Web App.png',
        tag: ['Laravel', 'TailwindCSS'],
        liveLink: '',
        codeLink: "https://github.com/darwisyf/laravel-akuntansi",
    }
])
</script>
<style>
.swiper-button-prev,
.swiper-button-next {
    cursor: pointer;
}

.swiper-slide {
    display: flex;
    justify-content: center;
    align-items: center;
}
</style>