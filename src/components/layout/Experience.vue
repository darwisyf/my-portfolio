<template>
    <section class="p-16">
        <header class="text-center">
            <h3 class="text-4xl font-bold text-primary dark:text-secondary">Experience</h3>
        </header>
        <ul class="mt-10 space-y-8 y-8">
            <li class="w-full rounded-xl shadow-lg border bg-gradient-to-t to-[#ACAC39] from-[#1F1E1C99]"
                v-for="(item, index) in Experience" :key="index">
                <article
                    class="flex flex-col lg:flex-row items-center lg:items-start rounded-[12px] bg-primary mt-[3px] mx-[3px] p-6 md:p-8 lg:p-10">
                    <figure class="w-full lg:w-1/4 flex justify-center lg:justify-start mb-4 lg:mb-0">
                        <Icon class="text-4xl md:text-6xl lg:text-7xl text-secondary" icon="mdi:office-building" />
                    </figure>

                    <section class="w-full lg:w-3/4 lg:pl-4 text-center lg:text-left">
                        <header>
                            <h3 class="text-xl md:text-2xl font-semibold uppercase text-secondary">{{ item.Title }}
                            </h3>
                            <p class="text-sm md:text-base text-white">{{ item.company }}</p>
                            <p class="text-sm md:text-base text-white">{{ item.duration }}</p>
                        </header>
                    </section>
                </article>
            </li>
        </ul>
    </section>
</template>
<script setup>
import { Icon } from '@iconify/vue';
import { ref } from 'vue';
const Experience = ref([
    {
        duration: '12/2024 - 01/2025',
        Title: 'Quality Assurance Intern',
        company: 'PT. Saptakarsa Prima'
    },
    {
        duration: '04/2025 - 07/2021',
        Title: 'Data Analyst Support Intern',
        company: 'PT. Toyota Motor Manufacturing Indonesia'
    },
    {
        duration: '09/2025 - 01/2026',
        Title: 'Data Entry Intern',
        company: 'PT. Hyper Mega Shipping'
    }
])
</script>
