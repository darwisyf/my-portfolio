<template>
    <section class="mt-32" id="skills">
        <SectionHeader title="My Skills" />
        <div class="mt-20 flex justify-center">
            <ul class="flex flex-wrap justify-center items-center">
                <li ref="skillRefs" v-for="(element, index) in skills" :key="index"
                    :class="`mx-[15px] rounded-[12px] mb-7 bg-gradient-to-t ${element.bgGradient}`">
                    <div class="rounded-[12px] bg-primary mt-[3px] p-12 md:p-5 text-center">
                        <h3 class="font-bold text-[35px] text-white flex items-center justify-center">
                            <Countup v-if="visibleItems[index]" :endVal="element.percentage" :startVal="0"
                                :duration="2" /> %
                        </h3>
                        <p class="font-normal text-[16px]" :style="{ color: element.textColor }">{{ element.title }}</p>
                    </div>
                </li>
            </ul>
        </div>
    </section>
</template>
<script setup>
import { ref, onMounted } from 'vue';
import SectionHeader from '@/components/UI/SectionHeader.vue';

const skills = ref([
    {
        percentage: 76,
        title: 'Figma',
        bgGradient: 'to-[#FF2C2C] from-[#FFE600]',
        textColor: '#FF2C2C'
    },
    {
        percentage: 73,
        title: 'VueJS',
        bgGradient: 'to-[#41b883] from-[#FFE600]',
        textColor: '#41b883'
    },
    {
        percentage: 87,
        title: 'Power BI',
        bgGradient: 'to-[#118DFF] from-[#FFE600]',
        textColor: '#118DFF'
    },
    {
        percentage: 67,
        title: 'Laravel',
        bgGradient: 'to-[#F05340] from-[#FFE600]',
        textColor: '#F05340'
    },
    {
        percentage: 78,
        title: 'Photoshop',
        bgGradient: 'to-[#40D0FF] from-[#FFE600]',
        textColor: '#40D0FF'
    },
    {
        percentage: 89,
        title: 'Excel',
        bgGradient: 'to-[#1D6F42] from-[#FFE600]',
        textColor: '#1D6F42'
    },
    {
        percentage: 95,
        title: 'HTML/CSS',
        bgGradient: 'to-[#FFFFFF] from-[#FFE600]',
        textColor: '#FFFFFF'
    },
    {
        percentage: 87,
        title: 'Javascript',
        bgGradient: 'to-[#F0DB4F] from-[#FFE600]',
        textColor: '#F0DB4F'
    },
]);

// Track visibility of items
const visibleItems = ref(skills.value.map(() => false));
const skillRefs = ref([]);

// Intersection Observer Logic
onMounted(() => {
    const observer = new IntersectionObserver(
        (entries) => {
            entries.forEach((entry) => {
                if (entry.isIntersecting) {
                    const index = skillRefs.value.indexOf(entry.target);
                    if (index !== -1) {
                        visibleItems.value[index] = true; // Mark item as visible
                    }
                }
            })
        },
        { threshold: 0.3 } // Trigger when 30% of element is visible
    );

    // Observe all skills elements
    skillRefs.value.forEach((el) => observer.observe(el));
})
</script>