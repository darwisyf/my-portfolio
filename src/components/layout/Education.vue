<template>
    <section class="p-16">
        <header class="text-center">
            <h3 class="text-4xl font-bold text-primary dark:text-secondary">Education</h3>
        </header>
        <ul class="mt-10 space-y-8 y-8">
            <li class="w-full rounded-xl shadow-lg border bg-gradient-to-t to-[#ACAC39] from-[#1F1E1C99]"
                v-for="(item, index) in Education" :key="index">
                <article
                    class="flex flex-col lg:flex-row items-center lg:items-start rounded-[12px] bg-primary mt-[3px] mx-[3px] p-6 md:p-8 lg:p-10">
                    <figure class="w-full lg:w-1/4 flex justify-center lg:justify-start mb-4 lg:mb-0">
                        <Icon class="text-4xl md:text-6xl lg:text-7xl text-secondary" icon="mdi:account-school" />
                    </figure>

                    <section class="w-full lg:w-3/4 lg:pl-4 text-center lg:text-left">
                        <header>
                            <h3 class="text-xl md:text-2xl font-semibold uppercase text-secondary">{{ item.School }}
                            </h3>
                            <p class="text-sm md:text-base text-white">{{ item.degree }}</p>
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
const Education = ref([
    {
        duration: '08/2019 - 07/2021',
        School: 'SMAN 109 Jakarta',
        degree: 'Science'
    },
    {
        duration: '08/2021 - Now',
        School: 'Unsika',
        degree: 'Informatics Engineering'
    }
])
</script>
